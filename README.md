# Hop in the project!

_Hop_ is a simple _bash_ script which quickly bootstraps project's 
dependencies described in the `.hop` file. _Hop_ uses `make`, and
_makefile_ formatted files.

## Installation

You can install _Hop_ by executing the following code snippet in your
terminal. If you don't have _cURL_ installed, then you must figure out 
on your own how to install it :P.

    $ TARGET=/usr/bin/hop sh -c 'curl -s https://raw.github.com/nu7hatch/hop/master/bin/hop | sudo tee $TARGET > /dev/null && sudo chmod +x $TARGET'

You may want to change the target path to get _Hop_ installed somewhere
else.

## Usage

To use _Hop_ you need to describe all the dependencies to be bootstrapped 
in the `.hop` file, in root directory of your project. The `.hop` files
use _makefile_ syntax to describe dependencies. Here's an example:

    all: redis mongodb
    
    mongo:
        sudo mongod -f /etc/mongod.conf
    redis:
        sudo systemctl start redis.service

When you have your `.hop` file ready, you just call `hop` command in the
project directory:

    $ cd ~/my/project/
    $ hop
    -----> Hopping in...
           sudo mongod -f /etc/mongod.conf
           forked process: 6246
           all output going to: /var/log/mongo/mongod.log
           sudo systemctl start redis.service
    
    -----> Fuck yeah!

_Hop_ will run everything you need to start working with the project at once.

## Copyright

Copyright 2012 (C) by Chris Kowalik (aka. nu7hatch)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public
License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program. If not, see http://www.gnu.org/licenses/.
