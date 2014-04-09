# TeleSMS

TeleSMS is a library for sending and receiving SMS messages with emails.
It uses carrier-provided email-to-sms gateways to send and receive messages.
To see a list of gateways, visit https://web.archive.org/web/20130906122931/http://en.wikipedia.org/wiki/List_of_SMS_gateways.

The purpose of this library is to encapsulate the code for sending and receiving 
email-to-sms messages since there are many edge cases. The goal is to maintain
the configuration and parsers to reduce the number of failed messages.

http://www.telefio.com

## Installation

Add this line to your application's Gemfile:

    gem 'telesms'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install telesms

## Usage

To send a message:

    # Order: FROM, TO, PROVIDER, BODY
    Telesms::Outgoing.deliver('john@example.com', '555555555', 'Verizon', 'Message body')

To receive and parse a message:

    Telesms::Incoming.receive(params[:mail])
    # => { from: '555555555', to: 'john@example.com', body: 'Message body', provider: 'Verizon' }

To get a list of available gateways:

    Telesms::Base.gateways
    # => { 'AT&T' => { sms: 'att.com', mms: 'mmode.com'}, ... }

## LICENSE:

(The MIT License)

Copyright (c) 2014 Telefio

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
