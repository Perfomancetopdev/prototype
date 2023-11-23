Sample and parameter for pushing message to queue.

#!/usr/bin/python

import pika

credentials = pika.PlainCredentials('guest', 'guest')

parameters = pika.ConnectionParameters('35.173.65.217',
                                   5672,
                                   '/',
                                   credentials)

connection = pika.BlockingConnection(parameters)

channel = connection.channel()

message = 'Python Queue - Message Sent from sender.py {N|T}'

channel.basic_publish(exchange='pluto',
                      routing_key='yellow',
                      body=message)
print(" [x] Sent 'Hello World!'")

connection.close()
