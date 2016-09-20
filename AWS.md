#IP=
#PEM=


ssh -i $PEM ec2-user@$IP  sudo yum update
ssh -i $PEM ec2-user@$IP  sudo yum install nginx

# locally:
cd ~/local/src/front-cover-aw.git/
jekyll build
scp -i $PEM -r _site/ ec2-user@$IP:/data/www/andreas-wilm/
scp -i $PEM nginx.conf ec2-user@$IP:/tmp
ssh -i $PEM ec2-user@$IP  sudo mv /tmp/nginx.conf /etc/nginx/nginx.conf
ssh -i $PEM ec2-user@$IP  sudo /etc/init.d/nginx restart




