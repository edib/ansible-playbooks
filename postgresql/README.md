#requirements

!! supposed that there is a postgresql server running out there.

```
# sudo apt-get install ansible postgresql libpq-dev python-psycopg2
```
when root 
```
# sudo -u postgres psql
postgres=# create user ansible with superuser --the username is subjective
postgres=# \passwd ansible 
```
#usage
must be used with tags otherwise "bad" things happen.
```
# ansible-playbook postgresql.yml --tags "create"
```

Ask for more!
http://stackoverflow.com/a/32118814/250296
