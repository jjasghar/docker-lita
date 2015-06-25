# docker-lita

You may want a simple container to start playing with [lita](http://lita.io).

This is an IRC lita container, but you could easily updated it for any other [lita-adapters](https://www.lita.io/plugins#adapters).

If you want to use IRC you should change the following to something in the [lita_config.rb](lita_config.rb):

```ruby
  config.robot.adapter = :irc
  config.adapters.irc.server = "irc.freenode.net"
  config.adapters.irc.channels = ["#ACHANNELYOUWANTOCHANGE"]
  config.adapters.irc.user = "botbot"
  config.adapters.irc.realname = "botbot"
  config.adapters.irc.password = "nopenotme"
  config.adapters.irc.cinch = lambda do |cinch_config|
    cinch_config.max_reconnect_delay = 123
  end
```

# Installation

Pre-step, clone down the repo:

```
git clone http://github.com/jjasghar/docker-lita
cd docker-lita
```

First, edit the [Gemfile](Gemfile) to have the lita plugins you want.

Second, configure the [lita_config.rb](lita_config.rb) for the plugins you want. (I've put the one's I like by default.)

Third, you should build the image yourself.

```
docker build -t="$USER/docker-lita" .
```

After it's built, all you have to do is:

```
docker run --name='litabot' -d $USER/docker-lita
```

Now you should see your bot in your channel within a couple seconds.

If you want to add a plugin or what not, do a `docker stop litabot` add the gem to the [Gemfile](Gemfile) then build again.

Then start it up and you should be good to go.

# Help/Suggestions

If you have any suggestions or ideas to help I'm all ears. This was created to just get a docker container standardized for the IRC bots I run. I wanted to pull things off Heroku and this was an easy way to have everything self contained.
