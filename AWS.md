hosted via s3
-------------

See [Hosting a Static Website](http://docs.aws.amazon.com/gettingstarted/latest/swh/getting-started-hosting-your-website.html)

Old: hosting on instance
--------------------------------
    
    #IP=
    #PEM=
    
    ssh -i $PEM ec2-user@$IP sudo yum update
    ssh -i $PEM ec2-user@$IP sudo yum install nginx
    
    cd ~/local/src/front-cover-aw.git/
    jekyll build    
    scp -i $PEM -r _site/ ec2-user@$IP:/data/www/andreas-wilm/
    scp -i $PEM nginx.conf ec2-user@$IP:/tmp
    ssh -i $PEM ec2-user@$IP sudo mv /tmp/nginx.conf /etc/nginx/nginx.conf
    ssh -i $PEM ec2-user@$IP sudo /etc/init.d/nginx restart
    



