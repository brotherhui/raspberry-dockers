# raspberry-dockers
nginx, phabricator, mysql


ALL the proposes are to use the local volume as the config and data path and use docker to start the server.


/data                 |    basic folder for all the dockers and data

all config folders and data folders for different servers are the default path plus /data

for example:

/etc/nginx/conf/conf.d  under /data/etc/nginx/conf/conf.d
