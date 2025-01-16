---
title: Tutorial: Chrome Plugin for Checking Consent Mode v2 Implementation
date: 2025-01-16
tags:
  - Tutorial
  - Cookies
  - Consent
  - Tracking
  - Chrome
  - Chrome Plugin
draft: false
summary: Build a Chrome plugin for Checking Consent Mode implementation!
authors:
  - Konrad
---

# Building a Chrome Plugin to check Consent Mode v2
## Introduction

Want to simplify checking consent mode v2? Build a Chrome plugin! Here’s a beginner-friendly guide to get started.

> [!note] This is a part of the Series: "Understanding cookies, consent, and future-proofing your tracking"

## What is a Chrome Plugin

A Chrome plugin (or extension) extends browser functionality. It can interact with web pages, making it ideal for automated tools like a CM v2 checker.

## Changes in Chrome Plugins Manifest v3

Chrome’s manifest v3 introduces:

- **Service workers**: Replaces background pages for improved performance and security.
    
- **DeclarativeNetRequest**: Provides safer ways to intercept and modify network requests.
    

## Getting started

1. **Set up your project folder**:
    
    - Create a folder named `consent-mode-checker`.
        
2. **Add manifest.json**:
    
    ```json
    {
      "manifest_version": 3,
      "name": "Consent Mode Checker",
      "version": "1.0",
      "permissions": ["activeTab"],
      "background": {
        "service_worker": "background.js"
      }
    }
    ```
    
3. **Create background.js**:
    
    ```js
    chrome.runtime.onInstalled.addListener(() => {
        console.log("Consent Mode Checker installed");
    });
    ```
    
4. **Load your extension**:
    
    - Open Chrome’s **Extensions** page (`chrome://extensions`).
        
    - Enable **Developer Mode** and click **Load unpacked**.
        
    - Select your folder.
        

## Step 2 (coming soon)

In the next step, we’ll add logic to detect `data-gcm-version="2.0"` and related parameters directly on web pages.

## TL;DR

Chrome plugins are a powerful way to automate tasks. Start by setting up a basic plugin, then expand its functionality to check for consent mode v2 specifics.