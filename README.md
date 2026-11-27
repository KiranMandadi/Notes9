OLD_JDK="/opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home"

NEW_JDK="/opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk/Contents/Home"

mv "$NEW_JDK/lib/security/cacerts" "$NEW_JDK/lib/security/cacerts.orig"

cp -L "$OLD_JDK/lib/security/cacerts" "$NEW_JDK/lib/security/cacerts"

"$NEW_JDK/bin/keytool" -list -cacerts -storepass changeit | head -3    # your team's password if different

org.gradle.java.installations.paths=/opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk/Contents/Home
