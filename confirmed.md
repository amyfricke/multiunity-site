---
layout: page
title: Email confirmed
permalink: /confirmed/
---

<!-- Where the MultiUnity sign-up confirmation email sends people. Supabase
     appends the sign-in tokens, or an error, to the address after "#"; that
     part never reaches this server, and the script below reads only the
     error code and then removes it from the address bar. -->

<div id="confirmed-ok" markdown="1">
Your email address is confirmed. Open MultiUnity and sign in with your email and password.
</div>

<div id="confirmed-error" hidden markdown="1">
This confirmation link has expired or was already used. If you already confirmed your email, open MultiUnity and sign in. If not, sign up again in the app to get a new link.
</div>

<p><a class="confirmed-open" href="multiunity://">Open MultiUnity</a></p>

If the button does nothing, open MultiUnity from your home screen. On a computer, open the app on your iPhone instead.

Don't have the app yet? [Join the iPhone beta on TestFlight](https://testflight.apple.com/join/KwwbkYwu).

<style>
  .confirmed-open {
    display: inline-block;
    padding: 0.6em 1.2em;
    border-radius: 999px;
    background: #2a7f78;
    color: #fff !important;
    font-weight: 600;
    text-decoration: none;
  }
</style>

<script>
  (function () {
    var params = new URLSearchParams(location.hash.slice(1) || location.search.slice(1));
    if (params.get('error') || params.get('error_code')) {
      document.getElementById('confirmed-ok').hidden = true;
      document.getElementById('confirmed-error').hidden = false;
    }
    // Drop the tokens Supabase appended so they are not left in history.
    if (location.hash || location.search) history.replaceState(null, '', location.pathname);
  })();
</script>
