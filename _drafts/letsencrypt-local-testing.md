# Testing LetsEncrypt Locally

## setup
https://github.com/letsencrypt/boulder
export GOPATH=~/gopath
git clone https://github.com/letsencrypt/boulder/ $GOPATH/src/github.com/letsencrypt/boulder
cd $GOPATH/src/github.com/letsencrypt/boulder

ip a s docker0 | grep "inet " | cut -d" " -f6 | cut -d"/" -f1
OR
ifconfig docker0 | grep "inet addr:" | cut -d: -f2 | awk '{ print $1}'

sed -i 's/FAKE_DNS: 127.0.0.1/FAKE_DNS: $ip_address/' docker-compose.yml

sed -i 's/"httpPort": 5002/"httpPort": 80/' test/config/va.json
sed -i 's/"httpsPort": 5001/"httpsPort": 443/' test/config/va.json

docker-compose up -d

## usage
certbot 127.0.0.1:4000

## verification

### firefox
[Temp profile][1] 
[Add cert to firefox][2]

### curl

curl -XGET -IL a.com --cacert $GOPATH/src/github.com/letsencrypt/boulder/test/test-root.pem
[Add cert to ubuntu][3]



Sources
[1]: https://community.letsencrypt.org/t/simple-boulder-server-setup/54669/7
[2]: https://unix.stackexchange.com/a/355899/95393
[3]: https://superuser.com/a/719047/377375