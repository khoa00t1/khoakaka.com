---
layout: default
title: Contact — Khoakaka
description: Reach out to Khoakaka about Family Tree or any of our apps.
permalink: /contact/
---

<section class="hero">
    <div class="container">
        <p class="eyebrow">Contact</p>
        <h1 class="hero__title">Get in touch</h1>
        <p class="hero__lede">
            Questions, feedback, or trouble with one of our apps? We read every message.
        </p>
    </div>
</section>

<section class="section">
    <div class="container prose">
        <h2>Support</h2>

        {% assign giapha = site.data.giapha %}
        {% if giapha.support_email and giapha.support_email != "" %}
            <p>
                Family Tree support:
                <a href="mailto:{{ giapha.support_email }}">{{ giapha.support_email }}</a>
            </p>
        {% else %}
            <p>
                A public support email will be added here once it's ready.
                In the meantime, please reach out via your platform's app store
                listing for Family Tree.
            </p>
        {% endif %}

        <h2>Legal</h2>
        <ul>
            <li><a href="{{ '/legal-policies/clan/privacy.html' | relative_url }}">Family Tree — Privacy Policy</a></li>
            <li><a href="{{ '/legal-policies/clan/terms.html' | relative_url }}">Family Tree — Terms of Use</a></li>
        </ul>
    </div>
</section>
