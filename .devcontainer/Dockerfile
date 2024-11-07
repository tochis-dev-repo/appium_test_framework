# Use the Java 17 image as a base
FROM mcr.microsoft.com/devcontainers/java:17-bullseye

# Install dependencies
RUN apt-get update && apt-get install -y \
    wget \
    unzip \
    lib32stdc++6 \
    lib32z1 \
    && rm -rf /var/lib/apt/lists/*

# Download and install Android SDK Command-line Tools
RUN mkdir -p /usr/local/android-sdk/cmdline-tools/latest \
    && cd /usr/local/android-sdk/cmdline-tools/latest \
    && wget https://dl.google.com/android/repository/commandlinetools-linux-8092744_latest.zip \
    && unzip commandlinetools-linux-8092744_latest.zip \
    && rm commandlinetools-linux-8092744_latest.zip

# Set environment variables
ENV ANDROID_HOME=/usr/local/android-sdk
ENV PATH=${PATH}:${ANDROID_HOME}/cmdline-tools/latest/bin:${ANDROID_HOME}/platform-tools

# Install platform tools, build tools, and a system image
RUN yes | ${ANDROID_HOME}/cmdline-tools/latest/bin/sdkmanager --licenses \
    && ${ANDROID_HOME}/cmdline-tools/latest/bin/sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"

