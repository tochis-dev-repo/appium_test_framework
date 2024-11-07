# appium_test_framework
The goal of this framework is to set up an appium test framework to showcase how a good framework should look like.

## We will be using:
- Java-Maven - to write our code and build our framework
- TestNG - to test our appium code
- a Sample apk - to explore some appium features for android testing
- a Sample ipa - to explore some appium features for iOS testing
- Github Codespaces to write our code
- AWS Device Farm to run our code (optional)
- GitHub Actions to deploy (optional)

## Methodology
I will be writing down my thoughts in the code, and in text files to guide myself on the tasks that need to be completed, and in certain cases, why I made certain decisions

###Appium Testing Environment Setup in GitHub Codespaces
In order to run appium code on codespace I had to install all the required dependencies one after the other. Here's how I did it.

#### Prerequisites

##### Step 1: Launch a Blank Codespace
Click on the Code button, select Codespaces, and start a New Codespace.
Once inside the blank Codespace, open the terminal.
> (this is an optional step, if you are using your local machine just open the terminal within your repo folder)

##### Step 2: Install Java Development Kit (JDK)
Update package lists and install Java JDK 17:
```bash
sudo apt update
sudo apt install -y openjdk-17-jdk
```
Verify the Java installation:
```bash
java -version
```
##### Step 3: Install Maven
Install Maven, which will manage dependencies in Java projects:
```bash
sudo apt install -y maven
```
##### Verify Maven installation:
```bash
mvn -version
```
##### Step 4: Install Node.js and NPM
Install Node.js and NPM, required for Appium:
```bash
sudo apt install -y nodejs npm
```
##### Verify Node.js and NPM installation:
```bash
node -v
npm -v
```
##### Step 5: Install Appium
Install Appium globally using NPM:
```bash
npm install -g appium
```
Verify Appium installation:
```bash
appium --version
```
##### Step 6: Install Android SDK Command-Line Tools
Create a directory for the Android SDK:
```bash
mkdir -p ~/android-sdk/cmdline-tools
```
Download the Android SDK command-line tools:
```bash
wget https://dl.google.com/android/repository/commandlinetools-linux-8092744_latest.zip -P ~/android-sdk/
```
Unzip the tools and set up the correct folder structure:
```bash
unzip ~/android-sdk/commandlinetools-linux-8092744_latest.zip -d ~/android-sdk/cmdline-tools
mv ~/android-sdk/cmdline-tools/cmdline-tools ~/android-sdk/cmdline-tools/latest
```
Set up environment variables for the Android SDK by adding them to .bashrc:
```bash
echo "export ANDROID_HOME=~/android-sdk" >> ~/.bashrc
echo "export PATH=\$PATH:\$ANDROID_HOME/cmdline-tools/latest/bin:\$ANDROID_HOME/platform-tools" >> ~/.bashrc
source ~/.bashrc
```

Accept SDK licenses and install platform tools and build tools:
```bash
sdkmanager --licenses
sdkmanager "platform-tools" "platforms;android-30" "build-tools;30.0.3"
```
##### Step 7: Verify the Installation
Verify sdkmanager:
```bash
sdkmanager --list
```
Test Appium (to see if it is properly installed):
```bash
appium
```
