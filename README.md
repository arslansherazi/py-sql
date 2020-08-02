# py-sql

## MySql Python Library
### pip install py-sql

#### OR
~~~
python3.7 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
~~~

#### Examples
~~~
py_sql = PySQL(host='127.0.0.1', port=3306, database='ofd_db', user='root', password='rootroot')
py_sql.query = '''
SELECT menu_item_id 
FROM favourite
WHERE user_id = %s
'''
py_sql.params = [user_id]
menu_items_data = py_sql.fetch_all()
~~~

~~~
py_sql = PySQL(**DB_CONFIGS)
py_sql.query = """
SELECT id 
FROM user
WHERE username = %s
"""
py_sql.params = [TEST_USER_USERNAME]
user = py_sql.fetch_one()
return user
~~~

~~~
py_sql = PySQL(**DB_CONFIGS)
py_sql.query = """
INSERT INTO dish(id, name, price, unit, image_url, small_image_url, created_date, updated_date, user_id)
VALUES(%s, %s, %s, %s, %s, %s, %s, %s, %s)
"""
py_sql.params = [
    0, faker.name(), 200, 'grams', '', '', datetime.now(), datetime.now(), user_id
]
py_sql.save_changes()
~~~