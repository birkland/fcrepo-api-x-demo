FROM tomcat:8.5-jre8

ENV FITS_VERSION=1.0.3 \
    FITS_WEB_VERSION=1.1.3
ENV FITS_HOME=/opt/fits-${FITS_VERSION}
 

# Fits home dir and dependencies
RUN mkdir -p ${FITS_HOME} \
    && apt-get update \
    && apt-get -y install file \
    && rm -rf /var/lib/apt/lists/*

# Fits core
RUN wget -O /opt/fits-${FITS_VERSION}.zip \
     http://projects.iq.harvard.edu/files/fits/files/fits-${FITS_VERSION}.zip \	
    && unzip /opt/fits-${FITS_VERSION}.zip -d /opt  \
    && rm /opt/fits-${FITS_VERSION}.zip

# Fits webapp
RUN  wget -O ${CATALINA_HOME}/webapps/fits.war \
 http://projects.iq.harvard.edu/files/fits/files/fits-${FITS_WEB_VERSION}.war \
    && echo "fits.home=${FITS_HOME}" \
     >> ${CATALINA_HOME}/conf/catalina.properties \
    && echo "shared.loader=\${fits.home}/lib/*.jar" \
     >> ${CATALINA_HOME}/conf/catalina.properties

    

