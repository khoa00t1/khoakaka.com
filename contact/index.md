---
layout: default
title: Contact — Khoakaka Studio
description: Reach out to Khoakaka Studio about Clan Tree or any of our apps.
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

        {% assign familytree = site.data.familytree %}
        <p>
            Clan Tree support:
            <a href="mailto:{{ familytree.support_email }}">{{ familytree.support_email }}</a>
        </p>
        {% if familytree.app_store_url and familytree.app_store_url != "" %}
            <p>
                You can also leave feedback on the
                <a href="{{ familytree.app_store_url }}" target="_blank" rel="noopener">App Store listing</a>.
            </p>
        {% endif %}

        <h2>Legal</h2>
        <ul>
            <li><a href="{{ '/legal-policies/familytree/privacy.html' | relative_url }}">Clan Tree — Privacy Policy</a></li>
            <li><a href="{{ '/legal-policies/familytree/terms.html' | relative_url }}">Clan Tree — Terms of Use</a></li>
            <li><a href="{{ '/legal-policies/familytree/delete-account.html' | relative_url }}">Clan Tree — Delete account</a></li>
        </ul>
    </div>
</section>
