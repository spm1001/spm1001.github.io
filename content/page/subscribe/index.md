---
title: "Subscribe"
url: "/subscribe/"
layout: "page"
---

Get new posts delivered to your inbox. No spam, unsubscribe anytime.

<script src="https://f.convertkit.com/ckjs/ck.5.js"></script>
<form action="https://app.kit.com/forms/8890024/subscriptions" method="post" data-sv-form="8890024" data-uid="cdd375a3d4" data-format="inline" data-version="5" class="subscribe-form seva-form formkit-form">
  <input type="email" name="email_address" placeholder="Your email address" required>
  <button type="submit" data-element="submit">Subscribe</button>
</form>

<style>
.subscribe-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 400px;
  margin: 2rem 0;
}

.subscribe-form input[type="email"] {
  padding: 0.875rem 1rem;
  font-size: 1rem;
  border: 2px solid var(--card-separator-color, #444);
  border-radius: 8px;
  background: var(--card-background, #424242);
  color: var(--card-text-color-main, #fff);
  outline: none;
  transition: border-color 0.2s ease;
}

.subscribe-form input[type="email"]:focus {
  border-color: var(--accent-color, #00c000);
}

.subscribe-form input[type="email"]::placeholder {
  color: var(--card-text-color-secondary, #999);
}

.subscribe-form button {
  padding: 0.875rem 1.5rem;
  font-size: 1rem;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  background: var(--accent-color, #00c000);
  color: var(--accent-color-text, #fff);
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.subscribe-form button:hover {
  opacity: 0.9;
}

@media (min-width: 500px) {
  .subscribe-form {
    flex-direction: row;
  }

  .subscribe-form input[type="email"] {
    flex: 1;
  }
}
</style>
