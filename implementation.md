## CMS Project - RB175

1. Getting Started - When a user visits the path "/", the application should display the text "Getting started."

Implementation: 
- create a cms.rb file
```
"require sinatra"
"require sinatra/reloader"

get "/" do
  "Getting started."
end
```

- create a `Gemfile` file
```
source "https://rubygems.org"

ruby "2.7.0"
gem "sinatra", "~>1.4.7"
gem "sinatra-contrib"
gem "erubis"
```
- create a `config.ru` file
```
require "./cms.rb"
run Sinatra::Application
```

- Run `bundle install` to install all dependencies and create a Gemfile.lock file
- Run `bundle exec ruby cms.rb`
---

2. Adding an Index page - When a user visits the home page, they should see a list of the documents in the CMS: history.txt, changes.txt and about.txt

Implentation:
- add `require "tilt/erubis"` Gemfile
- create a `views` directory
- create a `data` directory
- create three files, `about.txt`, `changes.txt`, `history.txt` within `data` directory
- within `cms.rb`, add this to GET method:
```
get "/" do
  @documents = Dir.glob("data/*").map do |doc| File.basename(doc)
  end

  erb :index
end
```

- Point `erb` to `:index` layout
- create a `index.erb` file within `data` directory
- within this file, add:

```
<ul>
  <% @documents.each do |doc| %>
    <li><%= doc %></li>
  <% end %>
</ul>
```

This creates a bulleted list of all the files within the `data` directory
---

3. Viewing Text Files 
- Make each document a link in the `views/index.erb` directory
- Add a `get "/:filename" route to allow us to view contents of documents
- Read the contents of documents within the file
- Set the value of the `Content-Type` header. This tells the browsers to display the response

4. 

