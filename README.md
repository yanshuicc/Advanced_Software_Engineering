# 作业说明
作业1地址
作业2地址
# note

###安装
ruby
sqlite3
rails
   gem install rails

###新建rails项目
rails new Advanced_Software_Engineering

###运行项目
rails server

###生成控制器Welcome
rails generate controller Welcome


### Creating the Article model
rails generate model Article title:string text:text

###数据库迁移
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
