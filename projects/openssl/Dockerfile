# Copyright 2016 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################

FROM gcr.io/oss-fuzz-base/base-builder
RUN apt-get update && apt-get install -y make
RUN git clone --depth 1 https://github.com/openssl/openssl.git
RUN cd $SRC/openssl/ && git submodule update --init fuzz/corpora
RUN git clone --depth 1 --branch openssl-3.0 https://github.com/openssl/openssl.git openssl30
RUN git clone --depth 1 --branch openssl-3.2 https://github.com/openssl/openssl.git openssl32
RUN git clone --depth 1 --branch openssl-3.3 https://github.com/openssl/openssl.git openssl33
RUN git clone --depth 1 --branch openssl-3.4 https://github.com/openssl/openssl.git openssl34
RUN git clone --depth 1 --branch openssl-3.5 https://github.com/openssl/openssl.git openssl35
RUN cd $SRC/openssl32/ && git submodule update --init fuzz/corpora
RUN cd $SRC/openssl33/ && git submodule update --init fuzz/corpora
RUN cd $SRC/openssl34/ && git submodule update --init fuzz/corpora
RUN cd $SRC/openssl35/ && git submodule update --init fuzz/corpora
WORKDIR openssl
COPY build.sh *.options replay_build.sh run_tests.sh $SRC/
ENV AFL_SKIP_OSSFUZZ=1
ENV AFL_LLVM_MODE_WORKAROUND=0
