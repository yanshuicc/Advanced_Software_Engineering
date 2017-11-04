# 作业说明
[作业地址](http://chenpei.science)
# note

### 安装
ruby

sqlite3

rails

gem install rails

### 新建rails项目
rails new Advanced_Software_Engineering

### 运行项目
rails server

### 生成控制器Welcome
rails generate controller Welcome


### Creating the Article model
rails generate model Article title:string text:text

### 数据库迁移
db/migrate/YYYYMMDDHHMMSS_create_articles.rb

	class CreateArticles < ActiveRecord::Migration[5.0]
	  def change
		create_table :articles do |t|
		  t.string :title
		  t.text :text
	 
		  t.timestamps
		end
	  end
	end

rails db:migrate

### Saving data in the controller

	def create
	  @article = Article.new(params[:article])
	 
	  @article.save
	  redirect_to @article
	end
	
### 服务器部署

sudo apt-get install apache2

sudo apt-get install passenger

sudo apt-get install libapache2-mod-passenger

sudo a2enmod passenger

sudo service apache2 restart

sudo a2ensite testapp

sudo service apache2 restart

	<VirtualHost *:80>
    ServerName example.com
    ServerAlias www.example.com
    ServerAdmin webmaster@localhost
    DocumentRoot /home/rails/testapp/public
    RailsEnv development
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
    <Directory "/home/rails/testapp/public">
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>

sudo chmod -R 777 ~/.bundle

sudo apt-get install nodejs

Generate secret key base

rake secret RAILS_ENV=production

Set environment variable

SECRET_KEY_BASE=<the-secret-key-base>

Restart the Rails app

touch /path/rails-app/tmp/restart.txt

参考这个链接：

http://stackoverflow.com/questions/29241053/incomplete-response-received-from-application-from-nginx-passenger

作者：kamionayuki
链接：http://www.jianshu.com/p/842727e8d17f
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。