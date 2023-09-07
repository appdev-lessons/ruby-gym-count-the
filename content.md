# Ruby Gym: Count "the"

Write a program that: Takes a `String`, then finds the number of times 'the' appears in the given String, and finally prints:
  ```
  "'the' appeared X times"
  ```

where `X` is an `Integer`.

Make sure each of the randomly `sample`d `sentence`s below outputs the correct response, then get the tests to pass.

Hint: It may be helpful to use the advanced `gsub` techniques with the `Regexp` class; see [the Ruby reference](https://learn.firstdraft.com/lessons/33-the-one-ruby-reference#advanced-gsub-techniques-with-regexp-class).

```ruby
sentences = [
  "the dog, the cat, the zebra, the giraffe",
  "the, the code, and the developer",
  "then the- their"
]
sentence = sentences.sample
# write your program below
```
{: .repl #count_the title="Count the" readonly_lines="[1,2,3,4,5,6,7]"}


```ruby
describe "Count the" do
  it "finds the 5 times when the string is 'the cabbage, the bagel, the apple, the drink, the bread'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("the cabbage, the bagel, the apple, the drink, the bread")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/appeared 5 times/), "Expected output to be ''the' appeared 5 times', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #count_the_test_1 for="count_the" title="Count the finds the 5 times when the string is 'the cabbage, the bagel, the apple, the drink, the bread'" points="1"}


```ruby
describe "Count the" do
  it "finds the 3 times when the string is 'the, beginning the end and the middle'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("the, beginning the end and the middle")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/appeared 3 times/), "Expected output to be ''the' appeared 3 times', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #count_the_test_2 for="count_the" title="Count the finds the 3 times when the string is 'the, beginning the end and the middle'" points="1"}


```ruby
describe "Count the" do
  it "finds the 2 times when the string is 'the- then, the'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("the- then, the")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/appeared 2 times/), "Expected output to be ''the' appeared 2 times', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #count_the_test_3 for="count_the" title="Count the finds the 2 times when the string is 'the- then, the'" points="1"}
