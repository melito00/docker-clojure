FROM clojure:openjdk-14-tools-deps-alpine
LABEL MAINTAINER Kenji Yamada <kenji.yamada@gmail.com>

ARG UID=501
ARG GID=100
ARG GROUPNAME=users
ARG USERNAME=kyamada

RUN echo "@testing http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
RUN apk --update --no-cache add bash rlwrap@testing
RUN adduser -u ${UID} -G ${GROUPNAME} -h /home/${USERNAME} -s /bin/bash -D ${USERNAME} \
  && echo ${USERNAME}:kyamada01 | chpasswd \
  && mkdir -p /home/${USERNAME}/.clojure \
  && chown ${USERNAME}:${GROUPNAME} /home/${USERNAME}/.clojure

ADD ./files/deps.edn /home/${USERNAME}/.clojure

USER ${USERNAME}
WORKDIR /home/${USERNAME}

CMD /bin/bash
