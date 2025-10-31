# Working on FastAPI-Restly

Or more correctly, _not enough_ working on FastAPI Restly.
Which is a REST framework, like the venerable DRF, but different.
The nice people at ClearBlue Markets allowed me to open source this part of the work that I did there.

It is such a pain to write CRUD in FastAPI. There are CRUD libraries out there, but when I was checking (almost two years ago now) I didn't like any of them.
So I wrote my own. It is not actually the first time I did this.
During my time at EclecticIQ, I wrote something similar for Flask, but flask-classy was doing part of the heavy lifting and writing a CRUD class from there was not so hard.
Still, you want steady patterns when tieing it together with SQLAlchemy and I got to nice declarative point which made me really happy.

```python
import fastapi_restly as fr

class ArticleView(fr.AsyncAlchemyView):
    prefix = "/articles"
    model = Article
    
```

This code gives CRUD. It creates several pydantic schemas under the hood, as well as a FastAPI router and several FastAPI endpoints. All of which can be overridden and customized.

I'm very happy with what I've got so far. But there is still plenty to do before I can publish it to PyPI. Primarily it needs a great deal of documentation. But I'd also like to add more tests; I really want it to be rock-solid and there are some features there that I don't fully trust yet.

This thing is actually in production at two companies where I worked. So it works, and it works well. But I've been the one applying it, and I'm sure other developers will use it in ways I didn't think of.
