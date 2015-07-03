command line
-------------

install bamble globally

    $ sudo npm install bamble -g

generate a 25 entry pad into book1

    $ bamble prep -n 25 --book book1

import the book1 pad

    $ cat books/book1 | bamble import

generate a message from that pad

    $ echo 'hello world' | bamble say -b book1 > filename.bamble

read a message from that pad

    $ cat filename.bambled | bamble read -b book1

## WARNING ##

each entry in the generated and imported pads is ONE TIME USE ONLY and are currently deleted at the time of using one to read a message.
Ideally this would happen after a little prompt interface, but for now it just happens as soon as you read. Be advised. 

Writing does not advance the pad, but it would need to be updated to remain in sync with the audience

there are more options described in the help section of the app and each of its subcommands

    $ bamble -h

    $ bamble say -h 

    $ bamble read -h 

and so on

api
---

in broad strokes...

install bamble locally

    $ npm install bamble 

    $ var Key = require('bamble/key')

    $ var newKey = new Key();

    $ var secret = newKey.secret; // this is what you would give to someone so they could read your message

    $ var message = Key.sign('this is a message') // this will output a message

    $ var key2 = new Key(secret)

    $ key2.read(message) //=> returns 'this is a message'


