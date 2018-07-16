p rocess m anager 2 runtime edition pm2 is a production runtime and process manager for node js applications with a built in load balancer it allows you to keep applications alive forever to reload them without downtime and facilitate common devops tasks starting an application in production mode is as easy as bash pm2 start app js pm2 is constantly assailed by more than 1800 tests official website https pm2 io doc works on linux stable macos stable windows stable all node js versions are supported starting node js 4 x installing pm2 bash npm install pm2 g npm is a builtin cli when you install node js installing node js with nvm start an application you can start any application node js python ruby binaries in path like that bash pm2 start app js your app is now daemonized monitored and kept alive forever more about process management container support with the drop in replacement command for node called pm2 runtime run your node js application in a hardened production environment using it is seamless run npm install pm2 g cmd pm2 runtime npm start read more about the dedicated integration managing applications once applications are started you can manage them easily to list all running applications bash pm2 list managing apps is straightforward bash pm2 stop app name id all json conf pm2 restart app name id all json conf pm2 delete app name id all json conf to have more details on a specific application bash pm2 describe id app name to monitor logs custom metrics application information bash pm2 monit more about application management cluster mode node js load balancing zero downtime reload the cluster mode is a special mode when starting a node js application it starts multiple processes and load balance http tcp udp queries between them this increase overall performance by a factor of x10 on 16 cores machines and reliability faster socket re balancing in case of unhandled errors starting a node js application in cluster mode that will leverage all cpus available bash pm2 start api js i processes processes can be max 1 all cpu minus 1 or a specified number of instances to start zero downtime reload hot reload allows to update an application without any downtime bash pm2 reload all seamlessly supported by all major node js frameworks and any node js applications without any code change more informations about how pm2 make clustering easy terminal based monitoring monitor all processes launched straight from the command line bash pm2 monit log management to consult logs just type the command bash pm2 logs standard raw json and formated output are available examples bash pm2 logs app name display app name logs pm2 logs json json output pm2 logs format formated output pm2 flush flush all logs pm2 reloadlogs reload all logs more about log management startup hooks generation pm2 can generates and configure a startup script to keep pm2 and your processes alive at every server restart init systems supported systemd upstart launchd rc d bash generate startup script pm2 startup freeze your process list across server restart pm2 save remove startup script pm2 unstartup more about startup hooks updating pm2 bash install latest pm2 version npm install pm2 latest g save process list exit old pm2 restore all processes pm2 update pm2 updates are seamless ready to scale go further with pm2 plus pm2 plus edition once you scale you need to make sure that your application is running properly without bugs performance issues and without downtimes thats why we created pm2 plus its a set of advanced features for both hardening the pm2 runtime and monitoring applications in production with pm2 plus you get a real time monitoring web interface smart exception reporting production profiling for memory and cpu pm2 runtime high availability fallback and much more like realtime logs custom metrics remote actions to start using pm2 plus via cli bash pm2 register or go to the application and create an account to discover pm2 plus register here pm2 plus features visual memory snapshots cpu flamegraphs multi server overview to discover pm2 plus register here pm2 plus expose custom metrics to get more insights on how your application behave plug custom metrics inside your code and monitor them with the pm2 monit command in your project install pm2 io pm bash npm install pm2 io save then plug a custom metric javascript const io require pm2 io let counter 1 const latency io metric name counter value function return counter setinterval counter 1000 pm2 plus module system pm2 embeds a simple and powerful module system installing a module is straightforward bash pm2 install module name here are some pm2 compatible modules standalone node js applications managed by pm2 pm2 logrotate automatically rotate logs and limit logs size pm2 server monit monitor the current server with more than 20 metrics and 8 actions changelog changelog contributors contributors license pm2 is made available under the terms of the gnu affero general public license 3 0 agpl 3 0 for other licenses contact us