---
layout: post
title: Missing out
---

**The first paragraph will be displayed as excerpt in the overview page. It can be long or short and no html tags will be processed.**

The next paragraph is the actual text.

<!-- https://gist.github.com/StephanHoyer/91d8175507fcae8fb31a
{% gist StephanHoyer/91d8175507fcae8fb31a %} -->

##### Ruby
{% highlight ruby linenos %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

C#
{% highlight csharp linenos %}
public class Klass
{
  public string id { get;set;}
  public Klass()
  {
    id = "123"; // just for testing
  }
}
{% endhighlight %}

Javascript
{% highlight javascript linenos %}
var Klass = function() {
  var id;
  new() {
    id = "123"; // just for testing
  }
}
{% endhighlight %}

Erlang
{% highlight erlang linenos %}
duplicate(0,_) ->
  [];
duplicate(N,Term) when N > 0 ->
  [Term|duplicate(N-1,Term)].
{% endhighlight %}

Elixir
{% highlight elixir linenos %}
parent = self()

# Spawns an Elixir process (not an operating system one!)
spawn_link(fn ->
  send parent, {:msg, "hello world"}
end)

# Block until the message is received
receive do
  {:msg, contents} -> IO.puts contents
end
{% endhighlight %}

F#
{% highlight fsharp linenos %}
let printRating book =
  match book.Rating with
  | Some rating ->
    printfn "I give this book %d star(s) out of 5!" rating
  | None -> printfn "I didn't review this book"
{% endhighlight %}
