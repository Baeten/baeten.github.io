---
layout: page
title: Contact
permalink: /contact/
nav: true
nav_order: 7
---

If you'd like to get in touch, please fill out the form below. I typically respond within 24-48 hours.

<style>
  .contact-card {
    background-color: var(--global-card-bg-color);
    border: 1px solid var(--global-divider-color);
    border-radius: 8px;
    padding: 2rem;
    margin-top: 2rem;
    box-shadow: 0 4px 6px rgba(0,0,0,0.05);
  }
  .contact-input {
    background-color: var(--global-bg-color);
    color: var(--global-text-color);
    border: 1px solid var(--global-divider-color);
    border-radius: 4px;
    padding: 0.75rem;
    width: 100%;
    margin-top: 0.5rem;
    transition: border-color 0.2s;
  }
  .contact-input:focus {
    outline: none;
    border-color: var(--global-theme-color);
  }
  .contact-btn {
    background-color: var(--global-theme-color);
    color: var(--global-bg-color); /* Ensures text is visible whether in light or dark mode */
    border: none;
    border-radius: 4px;
    padding: 0.75rem 1.5rem;
    font-weight: 600;
    cursor: pointer;
    margin-top: 1.5rem;
    transition: opacity 0.2s;
  }
  .contact-btn:hover {
    opacity: 0.8;
  }
  .contact-label {
    font-weight: 600;
    color: var(--global-text-color);
  }
</style>

<div data-fs-success class="alert alert-success mt-4" style="display: none; background-color: var(--global-card-bg-color); color: var(--global-text-color); border: 1px solid var(--global-theme-color);">
  <strong>Success!</strong> Thank you for reaching out. I will get back to you as soon as possible.
</div>
<div data-fs-error class="alert alert-danger mt-4" style="display: none;"></div>

<div class="contact-card">
  <form id="contact-form">
    <div style="margin-bottom: 1.5rem;">
      <label for="email" class="contact-label">Your Email Address</label>
      <input type="email" class="contact-input" id="email" name="email" placeholder="name@example.com" data-fs-field required />
      <span data-fs-error="email" style="color: #dc3545; font-size: 0.875rem; display: block; margin-top: 0.25rem;"></span>
    </div>

    <div>
      <label for="message" class="contact-label">Message</label>
      <textarea class="contact-input" id="message" name="message" rows="6" placeholder="Write your message here..." data-fs-field required></textarea>
      <span data-fs-error="message" style="color: #dc3545; font-size: 0.875rem; display: block; margin-top: 0.25rem;"></span>
    </div>

    <button type="submit" class="contact-btn" data-fs-submit-btn>Send Message</button>
  </form>
</div>

<script>
  window.formspree = window.formspree || function () { (formspree.q = formspree.q || []).push(arguments); };
  formspree('initForm', { formElement: '#contact-form', formId: 'mgogwbap' });
  
  // Show success alert when Formspree succeeds
  document.addEventListener('formspree:success', function() {
    const successAlert = document.querySelector('[data-fs-success]');
    const form = document.querySelector('#contact-form');
    if (successAlert) {
      successAlert.style.display = 'block';
    }
    if (form) {
      form.reset();
    }
  });
</script>
<script src="https://unpkg.com/@formspree/ajax@1" defer></script>
