Installation
============
Setup your environment first.  See https://github.com/gitkewl/setup.git for details.
The following commands are to be executed on your EC2 remote machine.

```sh
git clone https://github.com/gitkewl/bitstarter-postgres
cd bitstarter-postgres
./setup-ssjs.sh
```

Local and Remote Testing
========================
Once you have done this you will need to :
 
1. Edit the `.env` file to include your API key from
http://coinbase.com/account/integrations so that it looks like this:

```bash
[you@ec2~/bitstarter]$head .env
COINBASE_API_KEY=cb27e2ef0a8e872f792612d4d57937e70476ab8041455b00b35d1196cf80f50d
PORT=8080
```

2. Then you can run the server locally and preview at URLs like http://ec2-54-213-131-228.us-west-2.compute.amazonaws.com:8080 as follows:

```sh
foreman start
```

Try placing some orders and then going to the "/orders" URL at the top to
try it out. Note that you will get an "invalid api key" error if you didn't
do the `.env` step above.


3. For remote servers, deploy and push configuration variables

```sh
git push heroku master
heroku config:push
```

Then you can go to a URL like http://safe-dawn-4440.herokuapp.com and submit
orders to test it out. Note again that you will get an "invalid api key"
error if you didn't do the `.env` step above.

