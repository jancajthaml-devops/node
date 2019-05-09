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

FROM amd64/debian:stretch-slim

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8 \
    NODE_VERSION=10.11.0 \
    CC=gcc \
    CXX=g++

RUN apt-get update && \
    \
    apt-get install -y --no-install-recommends \
      apt-utils \
      ca-certificates \
      && \
    \
    apt-get -y install --no-install-recommends \
      git \
      curl \
      tar \
      cmake \
      make \
      patch \
      python \
      debhelper \
      config-package-dev \
      fakeroot \
      pkg-config \
      lintian \
      libsystemd-dev \
      gcc \
      g++ \
      libc6 \
      libc6-dev \
      \
      libzmq5>=4.2.1~ \
      libzmq3-dev>=4.2.1~ \
      && \
    \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN \
    curl -sL "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.gz" | tar xzf - -C /tmp && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-x64/bin/." /usr/bin/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-x64/lib/." /usr/lib/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-x64/include/." /usr/include/ && \
    \
    sed -i s/net.ipv4.ip_forward=0/net.ipv4.ip_forward=1/ /etc/sysctl.conf && \
    sed -i s/#net.ipv4.ip_forward/net.ipv4.ip_forward/ /etc/sysctl.conf

COPY --from=jancajthaml/jq /usr/local/bin/jq /usr/bin/jq
