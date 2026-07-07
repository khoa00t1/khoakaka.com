---
layout: default
title: About — Khoakaka Studio
description: Khoakaka Studio builds focused mobile apps that quietly do a lot of work for you.
permalink: /about/
---

<section class="hero">
    <div class="container">
        <p class="eyebrow">About</p>
        <h1 class="hero__title">Smart Code, Happy Life.</h1>
        <p class="hero__lede">
            {{ site.title }} is a small studio building focused mobile apps for
            Android, iOS and the Web. We like tools that get out of the way and
            quietly do a lot of work for you.
        </p>
    </div>
</section>

<section class="section">
    <div class="container prose">
        <h2>What we make</h2>
        <p>
            Right now we ship <a href="{{ '/products/familytree/' | relative_url }}">Clan Tree</a>,
            a genealogy app for extended families and clans. More apps will join the
            list under the same umbrella over time.
        </p>

        <h2>How we build</h2>
        <ul>
            <li>One Flutter codebase across Android, iOS and Web.</li>
            <li>Firebase for authentication, storage and the data layer.</li>
            <li>Subscriptions handled with care — no surprise charges.</li>
        </ul>

        <h2>Why</h2>
        <p>
            Our motto is <strong>{{ site.motto }}</strong>. We believe the best
            apps remove busywork instead of adding it.
        </p>
    </div>
</section>
