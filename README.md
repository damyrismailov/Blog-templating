# Flask Blog Templating

Small Flask app that renders a blog using Jinja templates. Posts are loaded from a JSON API, converted into `Post` objects, and displayed on an index page and individual post pages.

## Main features

- Fetches blog post data from a remote JSON endpoint using `requests`.
- Wraps each post in a `Post` class with `id`, `title`, `subtitle`, and `body` attributes.
- Renders an index page that:
  - loops over all posts
  - shows each post’s title and subtitle
  - links to a dedicated detail page for that post.
- Renders a post page that:
  - displays the selected post’s title, subtitle, and full body text
  - uses the same base styling as the index.
- Uses Jinja templating syntax in HTML files (`{{ }}` for variables, `{% %}` for loops) to inject data from Python.
- Static CSS file in `static/css/styles.css` for layout and typography.

## What I learned

- How to build a minimal Flask app and register routes with `@app.route`.
- How to call an external API with `requests.get()` and parse JSON data.
- How to create a simple model class (`Post`) and use it to structure incoming data.
- How to pass Python objects into templates via `render_template`.
- How to loop over data and access object attributes inside Jinja templates.
- How to connect routes that accept parameters (`/post/<int:index>`) and use those parameters to select a specific object.

## Project structure

- `main.py`  
  - Flask app entry point.  
  - Fetches posts from the API, builds `Post` objects list.  
  - Defines:
    - `/` route to render `index.html` with `all_posts`.
    - `/post/<int:index>` route to render `post.html` for a single post.
- `post.py`  
  - Defines the `Post` class with `id`, `title`, `subtitle`, and `body`.
- `templates/`  
  - `index.html` – index page that loops over `all_posts` and prints cards with title/subtitle and “Read” links.  
  - `post.html` – single-post page that shows the chosen post’s title, subtitle, and body.
- `static/css/styles.css`  
  - Styles for the blog wrapper, cards, typography, and footer.

## How to run

1. Clone the repo:

   git clone https://github.com/<your-username>/flask-blog-templating.git  
   cd flask-blog-templating  

2. (Optional) Create and activate a virtual environment:

   python -m venv venv  
   source venv/bin/activate   # Windows: venv\Scripts\activate  

3. Install dependencies:

   pip install -r requirements.txt  

   (At minimum you need `Flask` and `requests`.)

4. Run the app:

   python main.py  

5. Open the app in the browser:

   - Go to `http://127.0.0.1:5000` to see the index page with all posts.
   - Click “Read” on any card to open the individual post page at `/post/<id>`.
