# Gets Started

เขียน Blog ด้วย Ruby on rails

ที่มา [By Andy Leverenz](https://web-crunch.com/lets-build-with-ruby-on-rails-blog-with-comments/)

เริ่มด้วยคำสั่งแรก
~~~~ruby
rails new blog -d=postgresql && cd blog
~~~~

จะเห็นว่า ruby on rails สร้างเครื่องมือมาให้เราค่อนข้างพร้อมใช้งานในระดับหนึ่งแล้ว
เราลองมาทดสอบกันดูว่า ระบบยังทำงานได้ถูกต้องรึเปล่า
~~~~ruby 
rails db:create # create database
rails server # run server
~~~~
โอเคครับ ระบบยังทำงานได้ 
ต่อไปเรามาเตรียมเครื่องมือให้เราใช้งานได้สะดวกขึ้นอีกนะครับ

Gemfile
~~~~ruby
gem 'bulma-rails', '~> 0.7.4' # css framework
gem 'simple_form', '~> 4.1.0' # alternative html form develop for rails
# development
gem 'better_errors', '~> 2.5.1' # display error on web browser
~~~~
> เพิ่มเติม: find gem on https://rubygems.org/

ติดตั้ง package ต่าง ๆ
~~~~ruby
bundle install # install package
rails server # start server
rails generate simple_form:install # install simple from
~~~~
สร้าง controller posts 
~~~~ruby
rails g controller posts
~~~~
เพิ่มโค้ดไปที่ controllers/posts_controller.rb
~~~~ruby
def index; end
~~~~
config/routes.rb
~~~~ruby
resources :posts
root 'posts#index'
~~~~
เช็ค path ของระบบเรากันก่อน
~~~~ruby
rails routes
~~~~
create views/posts/index.html.erb
~~~~ruby
<h1>Hello Ruby on rails</h1>
~~~~
change application.css -> application.scss
~~~~ruby
@import 'bulma'
~~~~
ทดสอบการทำงาน http://localhost:3000/posts

เมื่อเรามี controller ไว้ติดต่อหน้าบ้านแล้ว เราก็ต้องมี model ไว้ติดต่อ database
~~~~ruby
rails g model post title:string content:string
rails db:migrate
~~~~
ต่อไป สร้าง create method controllers/post_controller.rb
~~~~ruby
def new
  @post = Post.new
end

def create
  @post = Post.new(post_params)
  if @post.save
    redirect_to @post # -> post_path(@post.id)
  else
    render 'new'
  end
end

private

def post_params
  params.require(:post).permit(:title, :content)
end
~~~~

views/new.html.erb
~~~~ruby
<div class="section">
  <%= simple_form_for @post do |f| %>
    <div class="field">
      <div class="control">
        <%= f.input :title, input_html: { class: 'input' }, wrapper: false, label_html: { class: 'label' } %>
      </div>
    </div>

    <div class="field">
      <div class="control">
        <%= f.input :content, input_html: { class: 'textarea' }, wrapper: false, label_html: { class: 'label' }  %>
      </div>
    </div>
    <%= f.button :submit, 'Create new post', class: "button is-primary" %>
  <% end %>
</div>
~~~~
ทดสอบ http://localhost:3000/posts/new


เมื่อเรากดสร้าง post จะเห็นได้ว่า โค้ด error
เอ... เป็นเพราะว่า post_path มันจะวิ่งไปที่ show และ เรายังไม่ได้ สร้างหน้า show.html.erb นั้นเอง

ก่อนที่เราจะสร้างหน้า show เราควรเพิ่ม method กันก่อน

controller/posts_controller.rb
~~~~ruby
def show
  @post = Post.find(params[:id])
end
~~~~

posts/show.html.erb
~~~~ruby
<% content_for :page_title, @post.title %>

<section class="section">
  <div class="container">
    <nav class="level">
      <!-- Left side -->
      <div class="level-left">
        <p class="level-item">
          <strong>Actions</strong>
        </p>
      </div>
      <!-- Right side -->
      <div class="level-right">
        <p class="level-item">
          <%= link_to "Edit", edit_post_path(@post), class:"button" %>
        </p>
        <p class="level-item">
          <%= link_to "Delete", post_path(@post), method: :delete, data: { confirm: "Are you sure?" }, class:"button is-danger" %>
        </p>
      </div>
    </nav>
    <hr/>

    <div class="content">
      <%= @post.content %>
    </div>
  </div>
</section>
~~~~
กด refresh ทดสอบการทำงาน
เมื่อ หน้า show ทำงานได้ ตามปกติแล้ว
ต่อไป มาสร้าง หน้า post list กันต่อ

controller/posts_controller.rb
~~~~ruby
def index
  @posts = Post.all.order('created_at DESC')
end
~~~~
posts/index.html.erb
~~~~ruby
<% content_for :page_title, 'Post list'%>

<section class='section'>
  <div class='container'>
    <% @posts.each do |post| %>
      <div class='card'>
        <div class='card-content'>
          <div class='media'>
            <div class='media-content'>
              <p class='title is-4'><%= link_to post.title, post %></p>
            </div>
          </div>
          <div class='content'>
            <%= post.content %>
          </div>
        </div>
      </div>
    <% end %>
  </div>
</section>
~~~~

ตกแต่งเพิ่มเติม

layouts/_header.html.erb
~~~~erb
<section class='hero is-primary is-medium'>
  <div class='hero-head'>
    <nav class='navbar'>
      <div class='container'>
        <div class='navbar-brand'>
          <%= link_to 'Blog', root_path, class: 'navbar-item' %>
          <span class='navbar-burger burger' aria-label='menu' aria-expanded='false' data-target='navbarMenuHeroA'>
            <span aria-hidden='true'></span>
            <span aria-hidden='true'></span>
            <span aria-hidden='true'></span>
          </span>
        </div>
        <div id='navbarMenuHeroA' class='navbar-menu'>
          <div class='navbar-end'>
            <%= link_to 'Create New Post', new_post_path, class:'navbar-item' %>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <div class='hero-body'>
    <div class='container has-text-centered'>
      <h1 class='title'>
        <%= yield :page_title %>
      </h1>
    </div>
  </div>
</section>
~~~~
layouts/application.html.erb
~~~~erb
<%= render 'layouts/header' %>
<%= yield %>
~~~~
js/application.js
~~~~js
document.addEventListener('DOMContentLoaded', () => {
  const $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);

  if ($navbarBurgers.length > 0) {

    $navbarBurgers.forEach( el => {
      el.addEventListener('click', () => {
        const target = el.dataset.target;
        const $target = document.getElementById(target);

        el.classList.toggle('is-active');
        $target.classList.toggle('is-active');
      });
    });
  }
});
~~~~
ต่อไป ลองมาเพิ่มหน้า edit และ delete 

อย่างที่บอกไปก่อนหน้านี้นะครับ เราต้องมี edit และ destroy method กันก่อน
~~~~ruby
def edit
  @post = Post.find(params[:id])
end

def update
  @post = Post.find(params[:id])

  if @post.update(post_params)
    redirect_to @post
  else
    render 'edit'
  end
end

def destroy
  @post = Post.find(params[:id])
  @post.destroy

  redirect_to posts_path
end
~~~~

posts/_form.html.erb
~~~~erb
<div class="section">
  <%= simple_form_for @post do |f| %>
    <div class="field">
      <div class="control">
        <%= f.input :title, input_html: { class: 'input' }, wrapper: false, label_html: { class: 'label' } %>
      </div>
    </div>

    <div class="field">
      <div class="control">
        <%= f.input :content, input_html: { class: 'textarea' }, wrapper: false, label_html: { class: 'label' }  %>
      </div>
    </div>
    <%= f.button :submit, 'Create new post', class: "button is-primary" %>
  <% end %>
</div>
~~~~
posts/new.html.erb
~~~~erb
<% content_for :page_title, "Create a Post" %>
<%= render 'form' %>
~~~~
posts/edit.html.erb
~~~~erb
<% content_for :page_title, "Edit Post" %>
<%= render 'form' %>
~~~~
กด refresh ทดสอบการทำงาน 

จบไปแล้วสำหรับ session เล็ก ๆ น้อย ๆ ครับ 
