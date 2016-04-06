---
layout: post
title: "Will_Paginate tip"
date: 2015-10-01 16:25:06
tags: gem will_paginate
---

# will_paginate last page

## controller
```
class PageantsController < ApplicationController
  @pageants = Pageant.all.order(id: :desc).paginate(:page => params[:page], :per_page => 4)
  #變量經過paginate宣告
end
```

## view (slim)
### 用divmod算出結果與頁數
```
= link_to t('wechat.home'), :action => 'vote', :page => 1
= will_paginate @fatigues, :container => false, :page_links => false
- case page = @pageants.total_entries.to_i.divmod(4)
- when page[1] == 0
  = link_to t('wechat.last'), :action => 'vote', :page => page[0]
- else
  = link_to t('wechat.last'), :action => 'vote', :page => page[0]+1
```

### 避免點擊分頁時params跟著帶到結果頁
```
= will_paginate @fatigues, :container => false, :page_links => false, :params => { :vote => '0' }
```
讓will_paginate帶參數時使用該數值{:vote => '0'}

