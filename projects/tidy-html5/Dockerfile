# Copyright 2018 Google Inc.
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

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        cmake ninja-build ruby-full && \
    apt-get clean

RUN git clone -b next --single-branch \
    https://github.com/htacg/tidy-html5.git tidy-html5
WORKDIR tidy-html5
RUN cd regression_testing && bundle2.7 install
COPY *.sh *.c *.h *.options $SRC/
