# unraid-deploy
This is GitHub action for achieving CI/CD on Unraid system

This is based on a PHP script from UNRAID forum [check here](https://forums.unraid.net/topic/40016-start-docker-template-via-command-line/)

``` php
#!/usr/bin/php
<?
$docroot = "/usr/local/emhttp";

require_once "$docroot/plugins/dynamix.docker.manager/include/DockerClient.php";

$var = parse_ini_file('/var/local/emhttp/var.ini');
$cfg = parse_ini_file('/boot/config/docker.cfg');

$driver = DockerUtil::driver();
$custom = DockerUtil::custom();
$subnet = DockerUtil::network($custom);

$opts = xmlToCommand($argv[1]);
$cmd = str_replace("create ","run -d ",$opts[0]);

passthru($cmd);
?>
```