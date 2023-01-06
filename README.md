# slip13


Q.1 Write a Java Program to implement an Adapter design pattern in mobile charger.
Define two classes – Volt (to measure volts) and Socket (producing constant volts of
120V). Build an adapter that can produce 3 volts, 12 volts and default 120 volts.
Implements Adapter pattern using Class Adapter 
Q.2. Write a Python program to prepare Scatter Plot for Iris Dataset 
Q.3. Using node js create a User Login System.



Q.1 Write a Java Program to implement an Adapter design pattern in mobile charger.
Define two classes – Volt (to measure volts) and Socket (producing constant volts of
120V). Build an adapter that can produce 3 volts, 12 volts and default 120 volts.
Implements Adapter pattern using Class Adapter 

:
class Volt {
 private int volts;
 public Volt(int v) { this.volts=v; }
 public int getVolts() { return volts; }
 public void setVolts(int volts) { this.volts = volts; }
}
 class Socket {
 public Volt getVolt(){ return new Volt(120); }
}
 interface SocketAdapter {
 public Volt get120Volt();
 public Volt get12Volt();
 public Volt get3Volt();
}
 class SocketClassAdapterImpl extends Socket implements SocketAdapter {
 @Override
 public Volt get120Volt() {
 return getVolt();
 }
 @Override
 public Volt get12Volt() {
 Volt v = getVolt();
 return convertVolt(v,10);
 }
 @Override 
 public Volt get3Volt() {
 Volt v = getVolt();
 return convertVolt(v,40);
 }
 private Volt convertVolt(Volt v, int i) {
 return new Volt(v.getVolts()/i);
 }
}
 class SocketObjectAdapterImpl implements SocketAdapter {
 // using composition for adapter pattern
 private Socket sock = new Socket();
 @Override
 public Volt get120Volt() {
 return sock.getVolt();
 }
 @Override
 public Volt get12Volt() {
 Volt v = sock.getVolt();
 return convertVolt(v,10);
 }
 @Override
 public Volt get3Volt() {
 Volt v = sock.getVolt();
 return convertVolt(v,40);
 }
 private Volt convertVolt(Volt v, int i) {
 return new Volt(v.getVolts()/i);
 }
}
public class Main {
 public static void main(String[] args) {
 testClassAdapter();
 testObjectAdapter();
 }
 private static void testObjectAdapter() {
 SocketAdapter sockAdapter = new SocketObjectAdapterImpl();
 Volt v3 = getVolt(sockAdapter,3);
 Volt v12 = getVolt(sockAdapter,12);
 Volt v120 = getVolt(sockAdapter,120);
 System.out.println("v3 volts using Object Adapter="+v3.getVolts());
 System.out.println("v12 volts using Object Adapter="+v12.getVolts());
 System.out.println("v120 volts using Object Adapter="+v120.getVolts());
 } 
private static void testClassAdapter() {
 SocketAdapter sockAdapter = new SocketClassAdapterImpl();
 Volt v3 = getVolt(sockAdapter,3);
 Volt v12 = getVolt(sockAdapter,12);
 Volt v120 = getVolt(sockAdapter,120);
 System.out.println("v3 volts using Class Adapter="+v3.getVolts());
 System.out.println("v12 volts using Class Adapter="+v12.getVolts());
 System.out.println("v120 volts using Class Adapter="+v120.getVolts());
 }
 private static Volt getVolt(SocketAdapter sockAdapter, int i) {
 switch (i){
 case 3: return sockAdapter.get3Volt();
 case 12: return sockAdapter.get12Volt();
 case 120: return sockAdapter.get120Volt();
 default: return sockAdapter.get120Volt();
 }
 }
} 


Q.2. Write a Python program to prepare Scatter Plot for Iris Dataset
:
import seaborn as sns
import matplotlib.pyplot as plt
from pandas.plotting import parallel_coordinates
import pandas as pd
# Parallel Coordinates
# Load the data set
iris = sns.load_dataset("iris")
parallel_coordinates(iris, 'species', color=('#556270', '#4ECDC4', '#C7F464'))
plt.show()


from pandas.plotting import andrews_curves
# Andrew Curves
a_c = andrews_curves(iris, 'species')
a_c.plot()
plt.show()



from seaborn import pairplot
# Pair Plot
pairplot(iris, hue='species')
plt.show()


from plotly.express import scatter_3d
# Plotting in 3D by plotly.express that would show the plot with capability of zooming,
# changing the orientation, and rotating
scatter_3d(iris, x='sepal_length', y='sepal_width', z='petal_length', size="petal_width",
                   color="species", color_discrete_map={"Joly": "blue", "Bergeron": "violet", "Coderre": "pink"})\
            .show()



q3)Using node js create a User Login System
:
//
//CSS
//Copy
//
* {
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, "segoe ui", roboto, oxygen, ubuntu, cantarell, "fira sans", "droid sans", "helvetica neue", Arial, sans-serif;
    font-size: 16px;
}
body {
    background-color: #435165;
}
.login {
    width: 400px;
    background-color: #ffffff;
    box-shadow: 0 0 9px 0 rgba(0, 0, 0, 0.3);
    margin: 100px auto;
}
.login h1 {
    text-align: center;
    color: #5b6574;
    font-size: 24px;
    padding: 20px 0 20px 0;
    border-bottom: 1px solid #dee0e4;
}
.login form {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    padding-top: 20px;
}
.login form label {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50px;
    height: 50px;
    background-color: #3274d6;
    color: #ffffff;
}
.login form input[type="password"], .login form input[type="text"] {
    width: 310px;
    height: 50px;
    border: 1px solid #dee0e4;
    margin-bottom: 20px;
    padding: 0 15px;
}
.login form input[type="submit"] {
    width: 100%;
    padding: 15px;
   margin-top: 20px;
    background-color: #3274d6;
    border: 0;
    cursor: pointer;
    font-weight: bold;
    color: #ffffff;
    transition: background-color 0.2s;
}
.login form input[type="submit"]:hover {
  background-color: #2868c7;
    transition: background-color 0.2s;
}

//
//HTML
//Copy
//
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width,minimum-scale=1">
		<title>Login</title>
        <!-- the form awesome library is used to add icons to our form -->
		<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.1/css/all.css">
        <!-- include the stylesheet file -->
        <link href="/style.css" rel="stylesheet" type="text/css">
	</head>
	<body>
		<div class="login">
			<h1>Login</h1>
			<form action="/auth" method="post">
				<label for="username">
					<!-- font awesome icon -->
					<i class="fas fa-user"></i>
				</label>
				<input type="text" name="username" placeholder="Username" id="username" required>
				<label for="password">
					<i class="fas fa-lock"></i>
				</label>
				<input type="password" name="password" placeholder="Password" id="password" required>
				<input type="submit" value="Login">
			</form>
		</div>
	</body>
</html>

//
//JS
//Copy
//
const mysql = require('mysql');
const express = require('express');
const session = require('express-session');
const path = require('path');

//
//SQL
//Copy
//
CREATE DATABASE IF NOT EXISTS `nodelogin` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
USE `nodelogin`;

CREATE TABLE IF NOT EXISTS `accounts` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `username` varchar(50) NOT NULL,
  `password` varchar(255) NOT NULL,
  `email` varchar(100) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

INSERT INTO `accounts` (`id`, `username`, `password`, `email`) VALUES (1, 'test', 'test', 'test@test.com');

//
//JS
//Copy
//
const connection = mysql.createConnection({
	host     : 'localhost',
	user     : 'root',
	password : '',
	database : 'nodelogin'
});

//
//JS
//Copy
//
const app = express();

//
//JS
//Copy
//
app.use(session({
	secret: 'secret',
	resave: true,
	saveUninitialized: true
}));
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'static')));

//
//JS
//Copy
//
// http://localhost:3000/
app.get('/', function(request, response) {
	// Render login template
	response.sendFile(path.join(__dirname + '/login.html'));
});

//
//JS
//Copy
//
// http://localhost:3000/auth
app.post('/auth', function(request, response) {
	// Capture the input fields
	let username = request.body.username;
	let password = request.body.password;
	// Ensure the input fields exists and are not empty
	if (username && password) {
		// Execute SQL query that'll select the account from the database based on the specified username and password
		connection.query('SELECT * FROM accounts WHERE username = ? AND password = ?', [username, password], function(error, results, fields) {
			// If there is an issue with the query, output the error
			if (error) throw error;
			// If the account exists
			if (results.length > 0) {
				// Authenticate the user
				request.session.loggedin = true;
				request.session.username = username;
				// Redirect to home page
				response.redirect('/home');
			} else {
				response.send('Incorrect Username and/or Password!');
			}			
			response.end();
		});
	} else {
		response.send('Please enter Username and Password!');
		response.end();
	}
});

//
//JS
//Copy
//
// http://localhost:3000/home
app.get('/home', function(request, response) {
	// If the user is loggedin
	if (request.session.loggedin) {
		// Output username
		response.send('Welcome back, ' + request.session.username + '!');
	} else {
		// Not logged in
		response.send('Please login to view this page!');
	}
	response.end();
});

//
//JS
//Copy
//
app.listen(3000);

//
//JS
//Copy
//
const mysql = require('mysql');
const express = require('express');
const session = require('express-session');
const path = require('path');

const connection = mysql.createConnection({
	host     : 'localhost',
	user     : 'root',
	password : '',
	database : 'nodelogin'
});

const app = express();

app.use(session({
	secret: 'secret',
	resave: true,
	saveUninitialized: true
}));
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(express.static(path.join(__dirname, 'static')));

// http://localhost:3000/
app.get('/', function(request, response) {
	// Render login template
	response.sendFile(path.join(__dirname + '/login.html'));
});

// http://localhost:3000/auth
app.post('/auth', function(request, response) {
	// Capture the input fields
	let username = request.body.username;
	let password = request.body.password;
	// Ensure the input fields exists and are not empty
	if (username && password) {
		// Execute SQL query that'll select the account from the database based on the specified username and password
		connection.query('SELECT * FROM accounts WHERE username = ? AND password = ?', [username, password], function(error, results, fields) {
			// If there is an issue with the query, output the error
			if (error) throw error;
			// If the account exists
			if (results.length > 0) {
				// Authenticate the user
				request.session.loggedin = true;
				request.session.username = username;
				// Redirect to home page
				response.redirect('/home');
			} else {
				response.send('Incorrect Username and/or Password!');
			}			
			response.end();
		});
	} else {
		response.send('Please enter Username and Password!');
		response.end();
	}
});

// http://localhost:3000/home
app.get('/home', function(request, response) {
	// If the user is loggedin
	if (request.session.loggedin) {
		// Output username
		response.send('Welcome back, ' + request.session.username + '!');
	} else {
		// Not logged in
		response.send('Please login to view this page!');
	}
	response.end();
});

app.listen(3000);




