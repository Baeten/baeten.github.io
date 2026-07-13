---
layout: cv
permalink: /cv/
title: Curriculum Vitae
nav: true
nav_order: 5
cv_pdf: /assets/pdf/CV.pdf # you can also use external links here
cv_format: rendercv # options: rendercv, jsonresume
description: 
toc:
  sidebar: left
---

<style>
  /* Fix horizontal scrolling and clipping on mobile devices for the CV timeline */
  @media (max-width: 576px) {
    /* Force the side-by-side timeline columns to stack vertically on small screens */
    .cv .list-group-item .row {
      display: flex !important;
      flex-direction: column !important;
    }
    
    /* Make both the date column and content column take 100% width */
    .cv .list-group-item .row > [class*="col-"] {
      max-width: 100% !important;
      width: 100% !important;
      flex: 0 0 100% !important;
      padding-left: 15px !important;
      padding-right: 15px !important;
    }
    
    /* Left-align the date badge so it doesn't try to center and overflow the left edge */
    .cv .date-column .d-flex {
      align-items: flex-start !important;
      margin-bottom: 0.5rem;
    }
    
    .cv .badge {
      white-space: normal !important;
      word-break: break-word;
      text-align: left !important;
    }
    
    /* Adjust location text to align left under the date */
    .cv .date-column .location {
      text-align: left !important;
    }
  }
</style>
