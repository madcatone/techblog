---
layout: post
title: "multiple destory with checkbox"
date: 2016-05-21 17:17:41
tags: gem destory
---

# 如何增加批次刪除？

## route.rb

```
  resources :blog_posts do
    collection do
      delete 'destroy_multiple'
    end
  end
```

## controller
```
def destroy_multiple

  BlogPost.destroy(params[:blog_posts])

  respond_to do |format|
    format.html { redirect_to blog_posts_path }
    format.json { head :no_content }
  end

end
```

### View
```
<%= form_tag destroy_multiple_blog_posts_path, method: :delete do %>
<table>
...
<td><%= check_box_tag "blog_posts[]", blog_post.id %></td>
...
</table>
<%= submit_tag "Delete selected" %>
<% end %>
```