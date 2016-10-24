# logstash-filter-ipip-free

插件开发官方文档：
https://www.elastic.co/guide/en/logstash/current/_how_to_write_a_logstash_filter_plugin.html

## 1.安装ruby 环境
（1）首先需要rvm环境， 具体参考： https://ruby-china.org/wiki/rvm-guide
> - $ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 
> - $ curl -sSL https://get.rvm.io | bash -s stable 
> - $ source ~/.bashrc 
> - $ source ~/.bash_profile
> - $ rvm list known

（2）安装jruby
> - rvm install jruby-9.0.5.0
> - rvm use jruby-9.0.5.0
> - gem install bundler
> - bundle install

测试
> - bundle exec rspec


## 2.build插件
> - $gem build logstash-filter-ipip.gemspec 

如果运行成功，会显示：
>   Successfully built RubyGem
>   Name: logstash-filter-ipip
>   Version: 2.0.0
>   File: logstash-filter-ipip-2.0.0.gem

## 3.修改 logstash中的Gemfile，安装到logstash
> gem "logstash-filter-ipip", "2.0.0", :path => "vendor/local_gems/ece69338/logstash-filter-ipip-2.0.0"

## 4.测试conf文件
将
> - 	geoip {
> - 		source => "ip"
> - 	}
> -     换成：
> - 	ipip {
> - 		source => "ip"
> - 	}

