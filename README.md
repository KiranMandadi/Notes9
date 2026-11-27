cd /opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk/Contents/Home/lib/security
mv cacerts cacerts.orig                                   # keep the original (safe even if it's a link)
cp ~/softwares/jdk-17.0.2/lib/security/cacerts cacerts    # the team's file; use its real location
keytool -list -cacerts -storepass changeit | head -3      # should list certificates