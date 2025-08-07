# House Points – App Brief (Agent-Ready)

## 📌 App Name
**House Points**

## 📱 Platform
- iOS-first using **React Native** (via Expo)  
- Supabase for backend (PostgreSQL, Auth, Cron)  
- Expo Notifications for push messages

## 🧭 App Overview
House Points is a gamified household task tracking app. It turns shared responsibilities into a point-based system, where users can earn and redeem points for custom or preset rewards. Optimised for two-person households, but supports 3+ users.

## 🧩 App Sections & Navigation

### HomePage
- Shows logged-in user’s:
  - Task cards (Permanent, Weekly, Monthly)
  - Weekly tick/line counters
  - Button → View Rewards  
  - Button → View Household

### RewardsPage
- Lists all redeemable rewards
- Shows cost in points
- Redeem button with confirmation
- Sends push notification to other user(s)

### HouseholdPage
- View all household members
- View others’ weekly progress

### AdminPanel (for owners only)
- Add/remove users
- Add/edit/remove tasks and rewards
- Assign user roles

## 🧹 Task Types
- **Permanent** – Always assigned
- **Weekly** – Auto-swaps weekly between users
- **Monthly** – Deep clean or seasonal tasks
- **Bonus** – Unassigned, voluntary tasks

## ✅ Task Mechanics
- ✔️ 1 point = task done once that week  
- ➕ 1 point = extra time or completing someone else’s task  
- ❌ Missed task penalty:
  - **2-person household**: other person gets +3 global points  
  - **3+ group**: user loses -1 global point

- Tasks reset weekly (via CRON)

## 🎯 Points & Rewards
- Points tracked per user and household
- Rewards:
  - Fully custom (name + point cost)
  - Pre-baked examples included
- Redemption:
  - Deducts points immediately
  - Sends notification to other user(s)

## 📈 Insights & Stats
- View past weeks and history
- Stats:
  - Task completion trends
  - Most frequent contributors
  - Preferred task types per person

## 🔔 Notifications
- App push notifications via Expo:
  - Daily log reminder
  - Weekly reset warning
  - Redemption alerts

## 👤 Profile & UI Design
- Avatars: uploaded or pre-generated (e.g., DiceBear)
- Homepage is **not bloated**:
  - Tasks view
  - Weekly progress
  - Points total
  - Buttons for Rewards + Household
- Charts and history live on separate screens

## 🛠 Tech Stack (Optimised for ChatGPT Agent)

| Layer        | Tool                          |
|--------------|-------------------------------|
| Frontend     | React Native (Expo)           |
| Backend      | Supabase                      |
| Auth         | Supabase (email login)        |
| Notifications| Expo Notifications            |
| Charts       | Victory Native / Chart Kit    |
| Avatars      | DiceBear                      |

## 🗃️ Supabase Schema (Simplified)

### Tables

- `users` (id, name, avatar, role, household_id)
- `households` (id, name, created_by)
- `tasks` (id, name, type, assigned_to, week, status, household_id)
- `task_logs` (id, user_id, task_id, completed_at, count)
- `points` (id, user_id, week, total_points, global_points)
- `rewards` (id, name, cost, created_by, household_id)
- `reward_redemptions` (id, reward_id, user_id, redeemed_at, notified_user_ids)

## ✅ Agent Task Summary

> Build a React Native (Expo) iOS app called **House Points** with a gamified task/reward system. Use Supabase for backend. Users log tasks to earn points, view stats, and redeem custom rewards. Build a clean UI with separate views for tasks, rewards, and household. Notifications remind users to log tasks or redeem rewards. Follow the logic and schema provided. Optimise flow for 2 users, but ensure flexibility for 3+.
