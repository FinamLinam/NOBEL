# Nobel

#### Video Demo: https://www.youtube.com/watch?v=QOBCoT9S00o


#### Description:



**What:** My project is a web-based application that displays famous quote and a pictures from Nobel Literature Prize winners of the past 20 years. Some quotes are about life and things larger than that life. Others are about smaller things, which are also about life and perhaps larger than that... Because everything is about life. Except for death.

**Why:** The point is to motivate people to read more books and other works from some of the best writers and authors in the world (according to the Nobel Institute).

**How:** Built in the online program Visual Studio Code for CS50. With the languages: HTML, Flask, CSS, SQL and Python.

**Walkthrough:**
NB: Since all the languages and files are interconnected, I will move back and forth a bit in my explanation.

Directory tree for project nobel:


Project
├── Static
│   ├── images
│   │   ├── abdulrazak_gurnah.jpg
│   │   ├── alice_munro.jpg
│   │   ├── (...)
│   │   └── tomas_transtromer.jpg
│   └── styles.css
├── templates
│   ├── index.html
│   └── laureate.html
├── app.py
├── insert_laureates.py
├── laureates.db
├── README.md
└── requirements.txt


The front page is called index.html, and it's where all the laureates are shown and categorized into containers. By clicking on one of them, the user will be sent to the second page called laureate.html. These two files are found in the templates folders. Since there are 20 different laureates in this project, and we dont want to have 20 different HTML pages (for reasons such as if we want to change something stylistic, we would have to change all of them), we use Flask to make the HTML pages dynamic. Hence, we only have two templates. But in reality, 1 + 20 = 21 different pages.

Flask is a microframework built in python. In the index file we use the placeholder {% for laureate in laureates %} which pulls data stored in a file called laureates.db. The .db file stands for database and is part of the SQL language. Here, all the content that we use to create the different dynamic html pages are stored.

To get from index.html to laureate.html, we use a link through Flask: 'laureate', id=laureate.id. It's the same concept in laureate.html as on the main page, just that it's only one id from the SQL file through Python and Flask. It shows the image {{ laureate.photo_url }}, title "Nobel Prize in Literature" with the {{ laureate.year }} and the quote from the {{ laureate.quote }}.

CSS (Cascading Style Sheets) is the language that handles the style and structure in this project, such as how the containers are placed, if there's shadow behind, the colors, and fonts. It is linked through the HTML files with its own file in the static folder called styles.css. In index.html it is integrated with Flask trough the code{{ url_for('static', filename='styles.css') }}. Furthermore we have two styles made in styles called .container and .lauretecard. And together with .header and .body that makes up the visual. The approach I have chosen is simplicity: black, grey and white. I want all the focus to be on the text and the imagination from the words, just like reading a novel. That's why the page may look boring at first glance because the magic is emphasized in the words - or behind the words.

Next to styles.css in the static folder we find the images. Here all the laureates have their pictures. It is important that the file name for the picture we use /static/images/firstname_lastname.jpg is the same as in the insert_laureates.py file.

The insert_laureates.py file is a Python file we use to insert or edit our laureates. I'm not completely sure why I did it this way, because it updates the db file, but if we update the .db file using SQL, the insert_laureates file will not update. So it's important that we only update our laureates.db through the python file. The positive aspect is that we can easily export the .db file with all the data from the site. Which we can also access this by typing sqlite3 laureates.db. in the terminal. Followed by .schema to see what's inside the file), and then SELECT * FROM laureates;

The last file app.py, is where the magic happens. Here the program imports the modules, connects SQLite database named laureates.db to CS50s module, and the apps does their things. In the @app.route('/'), the program calls for all the laureates from the SQL, and puts them in to index.html. And in the @app.route('/laureate/<int:id>'), it does the same thing for the other HTML file, just with the individual laureate like we talked about the first paragrapgh.


Summarized, I use Python to insert data in to a SQL file, and then HTML with Flask, CSS, and Python to display them them in a simplistic black, gray and white web page with the idea that words are for imagination, so we dont need the site to be super vizualised or graphic. For the future extra layers, extra layers can be added, but still in the same style. For example, add a seperate category for the other Nobel projects: Physics, Chemistry, Physiology or Medicine and Peace. Or expand the already existing category by adding more winners from earlier years. Or more quotes. Or explanation of the already existing quotes. But the main idea is that the page should work as a hook for peoples reading habits. For instance, if you read the quote from id 13 in the laureates.db file Tomas Tranströmer poem:

>In the middle of life, death comes
>to take your measurements.
>The visit is forgotten and life goes on.
>But the suit is being sewn on the sly.

This can make the reader think: "Hmm, what's this all about? Is it about realization, or a near-death experience, or someone else dying? I want to know more. I am curiosu. And that's the idea for this web-based application: To make someone want more literature.
# NOBEL
