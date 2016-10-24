# logstash-filter-ipip-free

1.安装ruby 环境
（1）首先需要rvm环境
参考： https://ruby-china.org/wiki/rvm-guide

$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 
$ \curl -sSL https://get.rvm.io | bash -s stable 
$ source ~/.bashrc 
$ source ~/.bash_profile
$ rvm list known

（2）安装jruby
rvm install jruby-9.0.5.0
rvm use jruby-9.0.5.0
gem install bundler
bundle install

2.build插件
# gem build logstash-filter-ipip.gemspec 
WARNING:  open-ended dependency on logstash-devutils (>= 0, development) is not recommended
  if logstash-devutils is semantically versioned, use:
    add_development_dependency 'logstash-devutils', '~> 0'
WARNING:  See http://guides.rubygems.org/specification-reference/ for help
  Successfully built RubyGem
  Name: logstash-filter-ipip
  Version: 2.0.0
  File: logstash-filter-ipip-2.0.0.gem

3.修改 logstash中的Gemfile，安装到logstash
gem "logstash-filter-ipip", "2.0.0", :path => "vendor/local_gems/ece69338/logstash-filter-ipip-2.0.0"

4.测试，将
	geoip {
		source => "ip"
	}
换成：
	ipip {
		source => "ip"
	}






