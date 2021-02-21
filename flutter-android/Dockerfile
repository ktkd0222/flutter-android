FROM circleci/android:api-30-node

# Install firebase tools
RUN sudo curl -sL https://firebase.tools | bash

# Install tools for easylauncher
RUN sudo apt-get update && sudo apt-get install -y fontconfig ttf-dejavu

# Install Flutter SDK
# ほぼ以下のファイルのコピペ。flutter_verisonの初期化とprecacheの部分は独自。
# https://github.com/cirruslabs/docker-images-flutter/blob/master/sdk/Dockerfile
ARG flutter_version=1.22.6

ENV FLUTTER_HOME=${HOME}/sdks/flutter \
    FLUTTER_VERSION=$flutter_version
ENV FLUTTER_ROOT=$FLUTTER_HOME

ENV PATH ${PATH}:${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin

RUN git clone --branch ${FLUTTER_VERSION} https://github.com/flutter/flutter.git ${FLUTTER_HOME}

RUN flutter precache

RUN yes | flutter doctor --android-licenses && flutter doctor