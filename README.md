
I have taken original from https://gitter.im/linnovate/mean


Modified to suite openshift

In package.json, added

"postinstall": " HOME=$OPENSHIFT_REPO_DIR  node tools/scripts/postinstall.js &&  HOME=$OPENSHIFT_REPO_DIR node node_modules/bower/bin/bower install "

1. bower install was failing due to some dependent module.
I logged to openshift command prompt and installed that dependent module.

2. A few more such issues sorted out similarly

3. EACCES issue.
Added below line 
httpServer.listen(process.env.OPENSHIFT_NODEJS_PORT, process.env.OPENSHIFT_NODEJS_IP);
in 
/var/lib/openshift/55ee880989f5cf7fdb0000bf/app-root/runtime/repo/node_modules/meanio/lib/core_modules/server/ExpressEngine.js

Note:-
This uses token based authentication. The original uses cookie based authentication.