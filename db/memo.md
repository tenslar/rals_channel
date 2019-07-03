## run

```bash
docker run --rm -v "$PWD"/rals_channel/db/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password -d -p 55544:3306 mysql:5.7
mysql -h 127.0.0.1 --port 55544 -u root -p

```