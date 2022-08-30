# Steps to generate a certificate with ssl :lock: 
These steps are to generate a ssl certificate in order to connect databases with the ssl option enable.

1. Run the command in a specific folder, for example in documents/sslGeneration

```
openssl req \
       -newkey rsa:2048 -nodes -keyout client.key \
       -x509 -days 365 -out client.crt
```
It will make you some questions, just reply all of them 

2. Then we have to extract the host and the port to generate the .cert file, for example in heroku in data.heroku.com we have all our databases and his credentials, so we need to know the **host** and the **port**. <br>
for example: 
```
host: ec2-54-172-yyy-xxx.compute-1.amazonaws.com
port: 5432
```
 
3. Run the followin script in the same location of the .crt and .key files
```
python config.py ec2-54-172-yyy-xxx.compute-1.amazonaws.com:5432  > server.crt
```

4. It will generates you a server.crt file! you are done.