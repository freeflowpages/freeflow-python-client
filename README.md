## Python client


#### Initialize

```python
from client import HumhubClient

client = HumhubClient(base_url='http://172.17.0.2', api_key='Riv5bNRAMEGJ4TR3s0GutEj7')
users = client.users
posts = client.posts
likes = client.likes
wikis = client.wikis
```

### User manipulation

```python
users.list()
users.get(user_id=1)
users.delete(user_id=1)
users.create(username='Required-field', email='Required-field', firstname='Required-field', lastname='Required-field', title=None, ..)
users.update(user_id=1, email='new-email', city='new-city', ..)
users.log_out(user_id=1)
```

### Post manipulation
```python
posts.list()
posts.list(space_id=1) # filter posts in certain namespace
posts.get(post_id=1)
posts.delete(post_id=1)
posts.create(space_id=2, message='Required-field')
posts.update(post_id=1,  message='Required-field')
```

### Likes manipulation
```python
likes.list() # all likes
likes.list(commnet_id=1) # likes for certain comment
likes.list(post_id=1) # likes for certain post
likes.list(wiki_page_id=1) # likes for certain wiki page

likes.get(like_id=1) # info about certain like (including what is being liked [post, comment,..]
likes.unlike(like_id=1) # unlike

likes.like(commnet_id=1) # like a comment
likes.like(post_id=1) # likes post
likes.like(wiki_page_id=1) # like a wiki page
```

### Wiki manipulation
```python
wikis.list() # all wiki pages
wikis.list(space_id=1) # all wiki pages in certain space
wikis.get(wiki_page_id=1) # get certain wiki page
wikis.delete(wiki_page_id=1) # delete certain wiki page
# create normal page in certain space
wikis.create(space_id='Required-space-id-integer', title='Required-field', content=None, is_category=False, parent_category_page_id=None, is_home=False, only_admin_can_edit=False, is_public=False)
# create category page (can have sub pages) in certain space 
wikis.create(space_id='Required-space-id-integer', title='Required-field', content=None, is_category=True, parent_category_page_id=None, is_home=False, only_admin_can_edit=False, is_public=False)
# create wiki page [Sub page/Child page] in another Category page
wikis.create(space_id='Required-space-id-integer', title='Required-field', content=None, is_category=False, parent_category_page_id='Parent-Category-page-id', is_home=False, only_admin_can_edit=False, is_public=False) 
# create page in personal space of user
wikis.create_personal(user_id='Required-user-id-integer', title='Required-field', content=None, is_category=False, parent_category_page_id='Parent-Category-page-id', is_home=False, only_admin_can_edit=False, is_public=False)
# Update wiki page
wiki.update(wiki_page_id='Required-wiki-page-id-integer', title='Required-field', content=None, is_category=False, parent_category_page_id=None, is_home=False, only_admin_can_edit=False, is_public=False) 
# Move certain wiki page into another space
wikis.move_to_space(space_id=1, wiki_page_id=1)
# Move certain wiki page into personal wiki for user
wikis.move_to_user_space(user_id=1)
```