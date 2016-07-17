---
layout: post
title: "module and class and extend"
date: 2016-05-21 15:57:24
tags: gem module class extend self
---

# class or instance_method?

## Example

```
module Food
  module Cake
    extend self
    def cream
      "Birthday cake!"
    end
  end
  class Drink
    def self.hot
      "Coffee!"
    end
  end
  class << self
    def cola
      "Coke or Peppsi?"
    end
  end
end
```

`Food::Cake.cream  => Birthday cake!`
`Food::Drink.hot  => Coffee!`
`Food.cola  => Coke or Peppsi?`