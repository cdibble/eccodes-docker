FROM kilobike/eccodes
MAINTAINER kilobike


RUN mkdir dwd \
&& cd dwd \
&& apt-get -y install unzip \
&& wget -O bufrtables_ecCodes.zip  "http://www.dwd.de/DE/leistungen/gds/help/schluessel_datenformate/bufrtables_ecCodes_zip.zip?__blob=publicationFile&v=2" \
    && unzip bufrtables_ecCodes.zip \
    && rm bufrtables_ecCodes.zip \
    && rsync -a bufr/  /usr/local/eccodes/share/eccodes/definitions/bufr/ \
    && rm -rf /dwd

ENTRYPOINT []
CMD []