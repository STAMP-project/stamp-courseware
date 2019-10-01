FROM jenkins/jenkins:lts

MAINTAINER Daniele Gagliardi <daniele.gagliardi@eng.it>

# Update Python to Python 3
USER root
RUN apt-get update && apt-get install -y python3 python3-pip libgomp1 maven && apt-get clean && \
	rm -f /usr/bin/python && ln -s /usr/bin/python3 /usr/bin/python && \
	ln -s /usr/bin/pip3 /usr/bin/pip

# Update pip and install dependencies needed to install CAMP
RUN pip install --upgrade pip
RUN pip install setuptools

# Install CAMP from setup script. Docker, Docker Swarm and last version of Z3 Solver are installed as well
RUN	curl -L https://github.com/STAMP-project/camp/raw/master/install.sh | bash -s -- --install-z3 --z3-version '4.7.1' --z3-python-bindings /usr/lib/python3.5 --install-docker && pip install setuptools

# drop back to the regular jenkins user
USER jenkins
