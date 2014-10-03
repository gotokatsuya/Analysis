Analysis
========

vagrantがインストールされている前提。  
私的動作環境：box = centos70  

$ vagrant box add centos70 http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.0_chef-provisionerless.box

# Install plugin  
$ vagrant plugin install vagrant-omnibus

# Login
$ vagrant up  
$ vagrant ssh

# How to use

$ vagrant ssh  
$ vi data.dat  
Ex) columns => user_id, fruit_id, rating_value  
1,101,5.0  
1,102,3.0  
1,103,2.5  
2,101,2.0  
2,102,2.5  
2,103,5.0  
2,104,2.0  
3,101,2.5  
3,104,4.0  
3,105,4.5  
3,107,5.0  
4,101,5.0  
4,103,3.0  
4,104,4.5  
4,106,4.0  
5,101,4.0  
5,102,3.0  
5,103,2.0  
5,104,4.0  
5,105,3.5  
5,106,4.0  

$ mahout recommenditembased --input data.dat --output output/ --similarityClassname SIMILARITY_PEARSON_CORRELATION

$ cat output/part-r-00000   
1	[104:3.9258494]  
3	[102:3.2698717]  
4	[102:4.7433763]  

Result : user_id=1にはfruit_id=104をrecommendすべき。予測ratingは3.9258494。

$ rm -rf output temp



# Error Tips

$ vagrant halt  
$ vagrant reload --provision


$ rm -rf Analysis/Analysis/berks-cookbooks  
$ berks vendor


http://railsapps.github.io/openssl-certificate-verify-failed.html

