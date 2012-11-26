#once, run jdconfig.rb
#worker cleanup

TODO:

1. re add airbrake
2. re add newrelic
3. fix asset_sync

#Resque.workers.each {|w| w.unregister_worker}

#how I deploy jd.com to heroku
git pull
git checkout joindiapsora
git rebase TAGNUMBER
bundle

git add .

git commit -am 'updating gemfile.lock'


heroku maintenance:on -a diaspora-production
ruby jdconfig.rb
git push heroku joindiaspora:master -f
heroku run 'rails runner "AssetSync.sync"'

heroku maintenance:off -a diaspora-production
