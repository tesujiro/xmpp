
start:
	jackal --config=$$GOPATH/src/github.com/ortuman/jackal/example.jackal.yml

db_start:
	mysql.server start

db_setup:
	# Grant right to a dedicated 'jackal' user
	echo "CREATE USER IF NOT EXISTS 'jackal'@'localhost' IDENTIFIED BY 'password';" | mysql -h localhost -u root
	echo "GRANT ALL ON jackal.* TO 'jackal'@'localhost';" | mysql -h localhost -u root
	# Create 'jackal' database
	echo "CREATE DATABASE jackal;" | mysql -h localhost -u jackal -p
	# Download lastest version of the MySQL schema from jackal Github repository.
	wget https://raw.githubusercontent.com/ortuman/jackal/master/sql/mysql.up.sql
	# Load database schema into the database.
	mysql -h localhost -D jackal -u jackal -p < mysql.up.sql
