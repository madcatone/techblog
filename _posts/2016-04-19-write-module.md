---
layout: post
title: "Write a Module"
date: 2016-04-19 23:08:07
tags: gem module map EvilTransform
---

# create module

## gaude and baidu map api

### lib/module/map.rb
```
require 'open-uri'
require 'json'

module MapModule
    class Amap #gaode map
        def to_geo(location_lng, location_lat)
            content = open(
                "http://restapi.amap.com/v3/geocode/regeo?key=" + "yourkey" +
                location_lng + "," + location_lat
            ).read
            result = JSON.parse(content)
            return address = {
                :location => result["regeocode"]["formatted_address"],
                :provimce => result["regeocode"]["addressComponent"]["province"].to_s,
                :city => result["regeocode"]["addressComponent"]["city"].to_s,
                :district => result["regeocode"]["addressComponent"]["district"].to_s,
                :township => result["regeocode"]["addressComponent"]["township"].to_s
            }
        end
    end
    class Bmap #baidu map
        def to_bgs(location_lng, location_lat)
            bd_location = EvilTransform
              .to_BGS(lat: location_lat.to_f, lon: location_lng.to_f)
            bd_lat = bd_location[0].to_s
            bd_lng = bd_location[1].to_s
            content = open(
                "http://api.map.baidu.com/geocoder?location=" +
                bd_lat + "," + bd_lng +
                "&coord_type=gcj02&output=json"
            ).read
            result = JSON.parse(content)
            return address = {
                :location => result["result"]["formatted_address"],
                :provimce => result["result"]["addressComponent"]["province"].to_s,
                :city => result["result"]["addressComponent"]["city"].to_s,
                :district => result["result"]["addressComponent"]["district"].to_s,
                :township => result["result"]["addressComponent"]["street"].to_s
            }
        end
    end
end
```