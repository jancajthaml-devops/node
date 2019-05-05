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

FROM arm32v7/debian:stretch-slim

ENV DEBIAN_FRONTEND=noninteractive \
    LANG=C.UTF-8 \
    NODE_VERSION=10.11.0 \
    CC=gcc \
    CXX=g++

RUN apt-get update && \
    \
    apt-get install -y --no-install-recommends \
      apt-utils \
      ca-certificates>=20161130 \
      && \
    \
    apt-get -y install --no-install-recommends \
      git>=1:2.11.0-3 \
      curl>=7.52.1-5 \
      tar=1.29b-1.1 \
      make=4.1-9.1 \
      cmake=3.7.2-1 \
      patch>=2.7.5-1 \
      python=2.7.13-2 \
      debhelper=10.2.5 \
      config-package-dev=5.1.2 \
      fakeroot=1.21-3.1 \
      pkg-config>=0.29-4 \
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
    curl -sL "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-arm64.tar.gz" | tar xzf - -C /tmp && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/bin/." /usr/bin/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/lib/." /usr/lib/ && \
      cp -a "/tmp/node-v${NODE_VERSION}-linux-arm64/include/." /usr/include/ && \
    \
    sed -i s/net.ipv4.ip_forward=0/net.ipv4.ip_forward=1/ /etc/sysctl.conf && \
    sed -i s/#net.ipv4.ip_forward/net.ipv4.ip_forward/ /etc/sysctl.conf

COPY --from=jancajthaml/jq /usr/local/bin/jq /usr/bin/jq
COPY --from=arm32v7/docker:18 /usr/local/bin/docker /usr/bin/docker
