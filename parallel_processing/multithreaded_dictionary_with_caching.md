# Multithreaded Dictionary with caching
Given a word, get the closest word in the dictionary based on levenstein's distance.
Cache this word for repeated access to aviod repeated computation.
Eveluate this is a multi-threaded scenario and make it thread safe.

## Dictionary
```ruby
class Dictionary
    attr_reader :dictionary

    def levenstein_distance(word)
        # use @dictionary to find closest word
    end

    def get_word(word)
        result_word = levenstein_word(word)
    end
end
```

## Dictionary with caching
```ruby
class Dictionary
    attr_accessor :dictionary, :cached_result

    def initialize()
        @cached_result = {}
    end

    def levenstein_distance(word)
        # Use @dictionary to get closest word
    end

    def get_word(word)
        cached_word, cached_closeset_word = @cached_result
        if cached_word == word
            return cached_result
        end

        closest_word = levenstein_word(word)
        @cached_result = {word, closest_word}

        closest_word
    end
end
```

## Thread-safe dictionary with caching
```ruby
class Dictionary
    attr_accessor :dictionary, :cached_result

    def initialize()
        @cached_result = {}
    end

    def levenstein_distance(word)
        # Use @dictionary to get closest word
    end

    def get_word(word)
        cached_word, cached_closeset_word = @cached_result

        synchronized do
            return cached_result if cached_word == word
        end

        closest_word = levenstein_word(word)

        synchronized do
            @cached_result = { word, closest_word }
        end

        closest_word
    end
end
```
