# Pairwise Parent - Implementation Plan

## Goal
Build a web app to choose a parent nickname through pairwise comparisons, using Bradley-Terry ranking.

## Tech Stack
- **Runtime**: Bun
- **Framework**: SvelteKit (handles both frontend and backend)
- **Database**: SQLite
- **Bradley-Terry**: Use a library for MVP (revisit later if we want to implement ourselves)

## Architecture
- **Backend**: SvelteKit server routes, serves pairings, stores comparison results
- **Frontend**: Svelte components (works on phone and desktop), shows two names, swipe/click to pick
- **Ranking**: Bradley-Terry model to estimate name strengths and uncertainties

## Components to Build

### 1. Data Layer
- SQLite database to store:
  - List of nicknames (loaded from nicknames.txt)
  - Comparison results (which name won each matchup)
  - Computed rankings/strengths (or compute on the fly?)

### 2. Backend API
- Endpoint to get next pairing (pick the most informative matchup based on uncertainty)
- Endpoint to submit a comparison result
- Endpoint to get current rankings

### 3. Frontend
- Display two names
- Swipe or click to choose preferred name
- Show current rankings

### 4. Bradley-Terry Logic
- Fit model to comparison data
- Get strength estimates + uncertainty for each name
- Use uncertainty to select next pairing

## Future / Out of Scope for MVP
- Phonetic grammar analysis and name generation
- Multiple users / separate rankings per user
- Implement Bradley-Terry ourselves for deeper understanding
