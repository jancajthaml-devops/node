# Copyright (c) 2017-2018, Jan Cajthaml <jan.cajthaml@gmail.com>
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# ---------------------------------------------------------------------------- #

FROM arm64v8/debian:stretch-slim

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8 \
    NODE_VERSION=10.11.0 \
    CC=gcc \
    CXX=g++

RUN apt-get update

RUN apt-get -y install --no-install-recommends \
    apt-utils

RUN apt-get -y install --no-install-recommends \
    ca-certificates

RUN apt-get -y install --no-install-recommends \
    git

RUN apt-get -y install --no-install-recommends \
    curl

RUN apt-get -y install --no-install-recommends \
    tar

RUN apt-get -y install --no-install-recommends \
    make

RUN apt-get -y install --no-install-recommends \
    cmake

RUN apt-get -y install --no-install-recommends \
    patch

RUN apt-get -y install --no-install-recommends \
    python

RUN apt-get -y install --no-install-recommends \
    debhelper

RUN apt-get -y install --no-install-recommends \
    config-package-dev

RUN apt-get -y install --no-install-recommends \
    fakeroot

RUN apt-get -y install --no-install-recommends \
    pkg-config

RUN apt-get -y install --no-install-recommends \
    libsystemd-dev

RUN apt-get -y install --no-install-recommends \
    gcc

RUN apt-get -y install --no-install-recommends \
    g++

RUN apt-get -y install --no-install-recommends \
    libc6

RUN apt-get -y install --no-install-recommends \
    libc6-dev

RUN apt-get -y install --no-install-recommends \
    libzmq5>=4.2.1~

RUN apt-get -y install --no-install-recommends \
    libzmq3-dev>=4.2.1~

RUN \
    curl -sL "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-arm64.tar.gz" | tar xzf - -C /tmp && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/bin/." /usr/bin/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/lib/." /usr/lib/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/include/." /usr/include/ && \
    \
    sed -i s/net.ipv4.ip_forward=0/net.ipv4.ip_forward=1/ /etc/sysctl.conf && \
    sed -i s/#net.ipv4.ip_forward/net.ipv4.ip_forward/ /etc/sysctl.conf

COPY --from=jancajthaml/jq /usr/local/bin/jq /usr/bin/jq
COPY --from=arm64v8/docker:18 /usr/local/bin/docker /usr/bin/docker
