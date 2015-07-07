# Alpine with an Oracle Java 8 installation 
# Based on develar/java

FROM alpine:3.2
MAINTAINER David Zarlengo <david@zarlengo.io>

ENV GLIBC_URL=https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk \
    GLIBC_BIN_URL=https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-bin-2.21-r2.apk \
    JRE8_TARBALL_URL=http://download.oracle.com/otn-pub/java/jdk/8u45-b14/server-jre-8u45-linux-x64.tar.gz \
    JRE8_TMP_DIR=jdk1.8.0_45

# about nsswitch.conf - see https://registry.hub.docker.com/u/frolvlad/alpine-oraclejdk8/dockerfile/

RUN   apk add --update curl ca-certificates \
 &&   cd /tmp \
 &&   curl -o glibc-2.21-r2.apk $GLIBC_URL \
 &&   apk add --allow-untrusted glibc-2.21-r2.apk \
 &&   curl -o glibc-bin-2.21-r2.apk $GLIBC_BIN_URL \
 &&   apk add --allow-untrusted glibc-bin-2.21-r2.apk \
 &&   /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib \
 &&   echo "curl: fetching $JRE8_TARBALL_URL" \
 &&   curl -jkSLH "Cookie: oraclelicense=accept-securebackup-cookie" $JRE8_TARBALL_URL \
      | gunzip -c - \
      | tar -xf - \
 &&   apk del curl ca-certificates \
 &&   mkdir /opt | true \
 &&   mv $JRE8_TMP_DIR/jre /opt/jre \
 &&   rm     /opt/jre/bin/jjs \
             /opt/jre/bin/keytool \
             /opt/jre/bin/orbd \
             /opt/jre/bin/pack200 \
             /opt/jre/bin/policytool \
             /opt/jre/bin/rmid \
             /opt/jre/bin/rmiregistry \
             /opt/jre/bin/servertool \
             /opt/jre/bin/tnameserv \
             /opt/jre/bin/unpack200 \
             /opt/jre/lib/ext/nashorn.jar \
             /opt/jre/lib/jfr.jar \
 &&   rm -rf /opt/jre/lib/jfr \
             /opt/jre/lib/oblique-fonts \
             /tmp/* \
             /var/cache/apk/* \
 &&   echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf

ENV JAVA_HOME /opt/jre
ENV PATH ${PATH}:${JAVA_HOME}/bin
ENV LANG C.UTF-8

ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/urandom"]
