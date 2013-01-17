# Dancer::Session::Redis

Redis backend for Dancer Session Engine

[![Build Status](https://travis-ci.org/Wu-Wu/Dancer-Session-Redis.png)](https://travis-ci.org/Wu-Wu/Dancer-Session-Redis)

- - - - - - - - - -

# VERSION

version 0.20

# INSTALLATION

To install this module type the following:

    perl Makefile.PL
    make
    make test
    make install

# SYNOPSIS

    # in the Dancer config.yml:
    session: 'Redis'
    redis_session:
        sock: '/var/run/redis.sock'
        password: 'QmG_kZECJAvAcDaWqqSqoNLUka5v3unMe_8sqYMh6ST'
        database: 1
        expire: 3600
        debug: 0
        ping: 5

    # or in the Dancer application:
    setting redis_session => {
        server   => 'redi.example.com:6379',
        password => 'QmG_kZECJAvAcDaWqqSqoNLUka5v3unMe_8sqYMh6ST',
        database => 1,
        expire   => 3600,
        debug    => 0,
        ping     => 5,
    };
    setting session => 'Redis';

# DESCRIPTION

This module is a Redis backend for the session engine of Dancer application. This module is a descendant
of [Dancer::Session::Abstract](http://search.cpan.org/perldoc?Dancer::Session::Abstract). A simple demo apllication might be found in the `eg/` directory of this
distribution.

# CONFIGURATION

In order to use this session engine, you have to set up a few settings (in the app or app's configuration file).

- session

    Set the vaue __Redis__. Required parameter.

- redis\_session

    Settings for backend.

    - _server_

        Hostname and port of the redis-server instance which will be used to store session data. This one is __required__ unless _sock_ is defined.

    - _sock_

        unix socket path of the redis-server instance which will be used to store session data.

    - _password_

        Password string for redis-server's AUTH command to processing any other commands. Optional. Check the redis-server
        manual for directive _requirepass_ if you would to use redis internal authentication.

    - _database_

        Database \# to store session data. Optional. Default value is 0.

    - _expire_

        Session TTL. Optional. Default value is 900 (seconds).

    - _ping_

        Time (in seconds) to check connection alive and re-establish in case of closed connection. Optional. Default value
        is 5 (seconds). Redis server close connection after a client is idle for seconds but server instance might be
        configured to not close client's connection. Check the redis server manual.

    - _debug_

        Enables debug information to STDERR, including all interactions with the redis-server. Optional. Default value is 0.

# METHODS

## init()

Validate settings and creates the initial connection to redis-server.

## create()

Creates a new object, runs `flush` and returns the object.

## flush()

Writes the session information to the Redis database.

## retrieve()

Retrieves session information from the Redis database.

## destroy()

Deletes session information from the Redis database.

# BUGS

Please report any bugs or feature requests through the web interface at
[https://github.com/Wu-Wu/Dancer-Session-Redis/issues](https://github.com/Wu-Wu/Dancer-Session-Redis/issues)

# SEE ALSO

[Dancer](http://search.cpan.org/perldoc?Dancer)

[Dancer::Session](http://search.cpan.org/perldoc?Dancer::Session)

[Storable](http://search.cpan.org/perldoc?Storable)

[Redis](http://search.cpan.org/perldoc?Redis)

[redis.io](http://redis.io)

# AUTHOR

Anton Gerasimov, <chim@cpan.org>

# COPYRIGHT AND LICENSE

Copyright (C) 2012 by Anton Gerasimov

This library is free software; you can redistribute it and/or modify it
under the same terms as Perl itself.