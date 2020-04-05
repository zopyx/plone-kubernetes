FROM python:3.7-slim-stretch
RUN useradd --system -m -d /plone -U -u 500 plone \
 && mkdir -p /plone/instance/ /data/filestorage /data/blobstorage


RUN buildDeps="dpkg-dev gcc libbz2-dev libc6-dev libffi-dev libjpeg62-turbo-dev libopenjp2-7-dev libpcre3-dev libssl-dev libtiff5-dev libxml2-dev libxslt1-dev wget zlib1g-dev" \
 && runDeps="gosu libjpeg62 libopenjp2-7 libtiff5 libxml2 libxslt1.1 lynx netcat poppler-utils rsync wv" \
 && apt-get update \
 && apt-get install -y --no-install-recommends $buildDeps 

WORKDIR /plone/instance
ADD buildout.cfg /plone/instance
ADD requirements.txt  /plone/instance
ADD bootstrap.py /plone/instance
CMD  ls -la 
CMD  ls -la  /plone
CMD  ls -la /plone/instance
CMD bash bootstrap.sh

EXPOSE 20100

CMD bin/zeo fg
