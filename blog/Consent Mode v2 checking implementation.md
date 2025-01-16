---
title: Consent Mode v2 Checking Implementation
date: 2025-01-16
tags:
  - Cookies
  - Consent
  - Tracking
draft: false
summary: Consent mode v2 (CM v2) enables websites to respect user consent while maintaining tracking functionalities for Google Ads, Analytics, and other tools.
authors:
  - Konrad
---
## Introduction

Consent mode v2 (CM v2) enables websites to respect user consent while maintaining tracking functionalities for Google Ads, Analytics, and other tools. Let’s explore how to verify its implementation and why it matters.

> [!NOTE] This is a part of the Series: "Understanding cookies, consent, and future-proofing your tracking"

## How to check (using dev tools)

1. **Open dev tools**: Access your browser’s developer tools (e.g., press `F12` or `Ctrl+Shift+I`).
    
2. **Check script tags**: In the **Elements** tab, search for `data-gcm-version="2.0"` in script tags.
    
3. **Inspect the network tab**: Navigate to the **Network** tab to monitor requests. Verify if the `ad_user_data` or `ad_personalization` parameters are present in your `dataLayer` or Google Tag Manager configurations.
    
4. **Look for errors**: Ensure there are no blocked or missing resources related to CM v2.
    

## Why consent mode v2 is needed

- **Improved analytics**: CM v2 enhances analytics accuracy even with partial user consent.
    
- **Regulatory compliance**: Aligns with GDPR and other data protection laws.
    
- **Marketing optimization**: Conversion modeling improves bidding algorithms and campaign performance.
    

## What happens if you don’t use it

Without CM v2:

- **Data gaps**: You lose valuable data for remarketing and conversions.
    
- **Performance drops**: Advertising campaigns may perform poorly.
    
- **Compliance risks**: Non-compliance with GDPR can lead to penalties.
    

## TL;DR

Consent mode v2 ensures compliance, accurate data, and better marketing outcomes. Double-check your implementation using browser tools to avoid pitfalls.