ARG SDC_VERSION=3.9.1
FROM streamsets/datacollector:${SDC_VERSION}

ARG SDC_LIBS
RUN "${SDC_DIST}/bin/streamsets" stagelibs -install="${SDC_LIBS}"
