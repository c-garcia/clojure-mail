# Clojure-mail

** IN PROGRESS **

[![Build Status](https://secure.travis-ci.org/owainlewis/clojure-mail.png?branch=master)](http://travis-ci.org/owainlewis/clojure-mail)

A clojure library mainly aimed at parsing, downloading and reading email from Gmail servers. 

Possible uses for this library include machine learning corpus generation and command line mail clients.

## Examples

In this example we'll log into a Gmail account and read messages from the inbox and spam folders.

```clojure

;; Create your auth creds

(auth! "user@gmail.com" "password")

;; Create a mail store instance. This is your gateway to your gmail account.

(def store (gen-store))

;; Now we can get 5 messages from our inbox

(def my-messages (take 5 (get-inbox)))

;; And read the first message in our inbox

(msg/read (first (get-inbox)))

;; Get 5 messages from the spam folder

(map #(msg/read %)
  (take 5 (get-spam)))

```

## Message parsing

Get all headers from an email 

```

;; Get an email message from our inbox

(def m (first (get-inbox)))

;; Returns all headers as a map

(msg/message-headers m)

;; Get the sender 

(msg/sender m)

;; Get the from address

(msg/from m)

```

## Unread messages

Fetch unread emails

```clojure

(unread-messages "INBOX")

```

## License

Copyright © 2012 FIXME

Distributed under the Eclipse Public License, the same as Clojure.
