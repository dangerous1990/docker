ARG SDC_VERSION=3.15.0
FROM streamsets/datacollector:${SDC_VERSION}

ARG SDC_LIBS
RUN "${SDC_DIST}/bin/streamsets" stagelibs -install="${SDC_LIBS}"
