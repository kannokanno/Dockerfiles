FROM centos:centos6

ENV PATH $PATH:/usr/bin

# install depend
RUN yum -y update
RUN yum -y install rpm-build tar gcc

# install daemontools
RUN cd /tmp
RUN curl -O http://www.qmailtoaster.com/download/stable/daemontools-toaster-0.76-1.3.6.src.rpm
RUN rpmbuild --rebuild daemontools-toaster-0.76-1.3.6.src.rpm
RUN mv /root/rpmbuild/RPMS/x86_64/daemontools-toaster-0.76-1.3.6.x86_64.rpm ./
RUN rpm -Uvh daemontools-toaster-0.76-1.3.6.x86_64.rpm

# setting init.d
RUN curl -O http://www.emaillab.org/djb/daemontools/svscan
RUN mv svscan /etc/init.d/
RUN chmod +x /etc/init.d/svscan
RUN /sbin/chkconfig --add svscan
RUN /sbin/chkconfig svscan on

# start daemontools
RUN /etc/init.d/svscan start
