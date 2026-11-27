echo 'export JAVA_HOME="/opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home"' >> ~/.bash_profile
echo 'export PATH="$JAVA_HOME/bin:$HOME/.remkit/bin:$PATH"' >> ~/.bash_profile
echo 'export JAVA_HOME="/opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home"' >> ~/.bashrc
echo 'export PATH="$JAVA_HOME/bin:$HOME/.remkit/bin:$PATH"' >> ~/.bashrc
launchctl setenv JAVA_HOME /opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home