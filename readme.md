<p align="center"><img src="https://res.cloudinary.com/dtfbvvkyp/image/upload/v1566331377/laravel-logolockup-cmyk-red.svg" width="400"></p>

<p align="center">
<a href="#"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="#"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="#"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="#"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>


## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such.

## CSRF Protection

##Introduction
##Excluding URIs
##X-CSRF-Token
##X-XSRF-Token

<p>Anytime you define an HTML form in your application, you should include a hidden CSRF token field in the form so that the CSRF protection middleware can validate the request. You may use the <code class=" language-php">@csrf</code> Blade directive to generate the token field:</p>
<pre class=" language-php"><code class=" language-php"><span class="token operator">&lt;</span>form method<span class="token operator">=</span><span class="token double-quoted-string string">"POST"</span> action<span class="token operator">=</span><span class="token double-quoted-string string">"/profile"</span><span class="token operator">&gt;</span>
    @csrf
    <span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token punctuation">.</span>
<span class="token operator">&lt;</span><span class="token operator">/</span>form<span class="token operator">&gt;</span></code></pre>

In addition to checking for the CSRF token as a POST parameter, the VerifyCsrfToken middleware will also check for the X-CSRF-TOKEN request header. You could, for example, store the token in an HTML meta tag:

<pre class=" language-php"><code class=" language-php"><span class="token operator">&lt;</span>meta name<span class="token operator">=</span><span class="token double-quoted-string string">"csrf-token"</span> content<span class="token operator">=</span><span class="token double-quoted-string string">"{{ csrf_token() }}"</span><span class="token operator">&gt;</span></code></pre>


Then, once you have created the meta tag, you can instruct a library like jQuery to automatically add the token to all request headers. This provides simple, convenient CSRF protection for your AJAX based applications:

<pre class=" language-php"><code class=" language-php">$<span class="token punctuation">.</span><span class="token function">ajaxSetup</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    headers<span class="token punctuation">:</span> <span class="token punctuation">{</span>
        <span class="token single-quoted-string string">'X-CSRF-TOKEN'</span><span class="token punctuation">:</span> $<span class="token punctuation">(</span><span class="token single-quoted-string string">'meta[name="csrf-token"]'</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">attr</span><span class="token punctuation">(</span><span class="token single-quoted-string string">'content'</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span></code></pre>