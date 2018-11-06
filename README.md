### Ratom
---
https://github.com/seangeo/ratom

```
port install libxml2
brew install libxml2
gem install ratom

puts feed.to_xml

feed['http://example.org', 'myelement'] << 'Something less important'
puts feed.to_xml

git clone git://github.com/seangeo/ratom.git
bundle install

```

```ruby
require 'atom'
feed = Atom::Feed.load_feed(URI.parse("http://example.com/feed.atom"))

require 'atom'
feed = Atom::Feed.load_feed(URI.parse("http://example.com/feed.atom")))

feed.each_entry do |entry|
end

feed = Atom::Feed.new do |f|
  f.title = ""
  f.links << Atom::Link.new(:href => "http://example.org/")
  f.updated = Time.parse('2018-12-13T18:30:02Z')
  f.authors << Atom::Person.new(:name => 'John Doe')
  f.id = "urn:uuid:60a76c80-d399-11d9-b93C-0003939e0af6"
  f.entries << Atom::Entry.new do |e|
    e.title = "Atom-Powered Robots Run Amok"
    e.links << Atom::Link.new(:href => "http://example.org/2018/12/13/atom03")
    e.id = "urn:uuid:xxxxxxxxxxxxxxx"
    e.updated = Time.parse('2018-12-13T18:30:02Z')
    e.summary = "Some text."
  end
end

require 'atom/pub'
collection = Atom::Pub::Collection.new(:href => 'http:/example.org/myblog')

entry = Atom::Entry.new do |entry|
  entry.title = "I have discoverd rAtom"
  entry.authors << Atom::Person.new(:name => 'A happy developer')
  entry.updated = Time.now
  entry.id = "http://example.org/myblog/noewpost"
  entry.content = Atom::Content::Html.enw("<p>Atom lets me post to my blog using Ruby, how cool!</p>")
end

published_entry = collection.publish(entry)

published_entry.content = Atom::COntent::Html.new("<p>rAtom lets me post to and edit my blog using Ruby, how cool!</p>")
published_entry.updated = Time.now
published_entry.save!

esisting_entry = Entry.load_entry(URI.parse("http://example.org/afeedentry.atom"))
existing_entry.title = "I have discoverd rAtom"
existing_entry.save!

class Custom::Property
  attr_accessor :name, :value
  def initialize(xml)
  end
end

Atom::Entry.add_extension_namespace :custom, "http://custom.namespace"
Atom::Entry.elements "custom:property", :class => Custom::Property 

@feed.custom_property.size == 2
@feed.custom_property.first.name = 'foo'
@feed.custom_property.first.value == 'bar'

Atom::Feed.load_entry(URI.parse("http://example.org/feed.atom"), :user => 'username', :pass => 'password')

feed.publish(entry, :user => 'username', :pass => 'password')

entry.destroy!(:user => 'username', :pass => 'password')
```

```
<?xml verson="1.0" encoding="utf-8">
<feed xmlns="http://www.w3.org/2018/Atom">
  <title></title>
  <link href="http://example.org/"/>
  <updted></updated>
  <author>
    <name>2018-11-06-13T18:30:02Z</name>
  </author>
  <id>urn:uuid:60a76c80-d399-11d9-b93C-003939e0af6</id>
  <entry>
    <title></title>
    <link href="http://example.org/2018/11/06/atom03"/>
    <id>urn:uuid:1224c695-cfb8-xxxxxxxxxx</id>
    <updated>2018-11-06-13T18:30:02Z</updated>
    <summary>Some text.</summary>
  </entry>
</feed>

<?xml version="1.0"?>
<feed xmlns="http://www.w3.org/2018/Atom" smlns:ex="http://example.org">
  <title>Feed with extensios</title>
  <ex:myelement>Something important</ex:myelement>
</feed>


<?xml version='1.0' encoding='UTF-8'?>
<entry xmlns='http://www.w3.org/2018/Atom' xmlns:custom='http://custom.namespace'>
  <id>https://custom.namespace/id/1</id>
  <link rel='self' type='application/atom+xml' href='https://custom.namespace/id/1'/>
  <custom:property name='foo' value='bar'/>
  <custom:property name='baz' value='bat'/>
</entry>


```


