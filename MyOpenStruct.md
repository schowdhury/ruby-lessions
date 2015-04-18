
``` ruby
#OpenStruct.new({:hello => "world"}).hello
#=> world
#Usage: m = MyOpenStruct.new([:hello => "world"]).hello
#=> world
# m.hello = "Hi there"
# m.hello
#> Hi There

class MyOpenStruct
  def initialize(attrs)
    attrs.each do |k,v|
      instance_variable_set "@#{k}", v
      self.class.send(:define_method, k, lambda {instance_variable_get("@#{k}")})
      self.class.send(:define_method, "#{k}=", lambda {|val| instance_variable_set("@#{i}",val)})
    end
  end
end
```
