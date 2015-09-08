
I have taken original from 
[![Build Status](https://travis-ci.org/linnovate/mean.svg)](https://travis-ci.org/linnovate/mean)
[![Dependencies Status](https://david-dm.org/linnovate/mean.svg)](https://david-dm.org/linnovate/mean)
[![Gitter](https://badges.gitter.im/JoinChat.svg)](https://gitter.im/linnovate/mean?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Modified to suite openshift
In package.json, added
"postinstall": " HOME=$OPENSHIFT_REPO_DIR  node tools/scripts/postinstall.js &&  HOME=$OPENSHIFT_REPO_DIR node node_modules/bower/bin/bower install "

bower install was failing due to some dependent module.
I logged to openshift command prompt and installed that dependent module.

A few more such issues sorted out similarly

EACCES issue.
Added below line 
httpServer.listen(process.env.OPENSHIFT_NODEJS_PORT, process.env.OPENSHIFT_NODEJS_IP);
in 
/var/lib/openshift/55ee880989f5cf7fdb0000bf/app-root/runtime/repo/node_modules/meanio/lib/core_modules/server/ExpressEngine.js

Note:-
This uses token based authentication. The original uses cookie based authentication.