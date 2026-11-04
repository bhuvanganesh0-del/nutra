# NutriSnap — AI Food Calorie & Nutrition Tracker

A mobile-first, iPhone-optimized PWA for AI-powered food tracking. Single-file app — no build step.

## Quick start
1. Host `index.html` over HTTPS (GitHub Pages, Netlify, or Vercel — all free). HTTPS is required for camera access on iPhone Safari.
2. Open the URL in Safari → Share → **Add to Home Screen**.
3. Open from the home screen icon — it runs full-screen like a native app.

## Enabling real AI photo recognition (Gemini)
Without a key, scanning falls back to **manual confirmation with suggested items** — the app still works end-to-end.
1. Get a free API key at **aistudio.google.com**.
2. In the app: **Profile → AI Vision API → paste key → Save**.
3. The key is stored only in your device's browser (localStorage) and is sent directly to Google's API from your device. It is never sent anywhere else.

**For production use:** route API calls through your own backend (e.g., a Vercel/Cloudflare serverless function) so keys stay server-side. Never ship keys in public client code.

## What's inside (all functional)
- **AI food scanner** — camera capture (iPhone `capture="environment"`) + photo upload, AI multi-item identification, portion estimation, correction flow, manual entry. Every value labeled **ESTIMATE**.
- **Dashboard** — calorie ring vs goal, protein/carbs/fats/fiber progress bars, Breakfast/Lunch/Snacks/Dinner sections, water tracker, streak.
- **Diary** — meals saved with photos, edit (name/kcal rescale) & delete, daily/weekly/monthly filters, meal history.
- **Protein tracker** — grams vs target, remaining, protein-rich food chips.
- **AI assistant** — answers protein-today, top-protein meal, balanced meal ideas, nutrient breakdowns, weekly summaries, water & streak status. Uses Gemini if a key is set, otherwise a full local engine.
- **Extras** — food comparison tool, smart suggestions based on remaining targets, weekly calorie/protein charts (canvas), healthy alternatives for any food, streak tracking, dark/light mode, JSON data export.

## Nutrition data
Built-in database of ~85 common foods with typical USDA-based values per 100 g. Calculations scale by portion grams. These are estimates, not lab values — the UI says so everywhere.

## Backend note
This version uses the browser's localStorage as its database (works offline, zero setup). For multi-device sync and social features, add a backend (Supabase or Firebase are the quickest: swap the `load()`/`save()` functions for API calls).
