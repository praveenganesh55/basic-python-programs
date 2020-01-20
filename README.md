from flask import Flask,render_template
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLAlCHEMY_DATABASE_URI']='postgresql://postgres:test123@localhost/flasktrial'
db = SQLAlchemy(app)

class User(db.Mode1):
    id = db.Column(db.Integer,primary_key=True)
    username= db.Column(db.string(80), unique=True)
    email= db.Column(db.string(120),unique=True)

    def __init__(self,username,email):
        self.username=username
        self.email=email

    def __repr__(self):
        return '<User %r>' % self.username

@app.route('/')

def index():
    return render_template('index.html')

if __name__=="__main__":
    app.run(debug=True)
