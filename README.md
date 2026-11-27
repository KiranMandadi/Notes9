JH="$(brew --prefix openjdk@21)/libexec/openjdk.jdk/Contents/Home"
echo "$JH"        # check this folder is your JDK 21

for f in ~/.bash_profile ~/.bashrc; do
  printf '%s\n' "export JAVA_HOME=\"$JH\"" \
    'export PATH="$JAVA_HOME/bin:$HOME/.remkit/bin:$PATH"' >> "$f"
done

launchctl setenv JAVA_HOME "$JH"