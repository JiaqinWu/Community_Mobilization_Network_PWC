# Supabase Setup Instructions

Your app now has Supabase integration! Follow these 3 steps to enable persistent storage:

## Step 1: Create the Supabase Table

1. Go to https://app.supabase.com
2. Select your project
3. Click **SQL Editor** → **New query**
4. Copy and paste ALL content from `supabase_setup.sql`
5. Click **Run** (Cmd+Enter or Ctrl+Enter)
6. You should see "Success. No rows returned" ✅

## Step 2: Add Environment Variables to Render

1. Go to https://dashboard.render.com
2. Select your service
3. Click **Environment** tab
4. Add these **3** environment variables:

| Key | Value |
|-----|-------|
| `SUPABASE_URL` | `https://xkokabzojvuuwnntbxxs.supabase.co` |
| `SUPABASE_KEY` | `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Inhrb2thYnpvanZ1dXdubnRieHhzIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjE5MDY2MTcsImV4cCI6MjA3NzQ4MjYxN30.jMy7J_tR-mu4NoIvpaHIbferJq7_SHuqt_8EuYQ1gFw` |
| `SUPABASE_TABLE` | `organization_overlays` |

5. Click **Save Changes**
6. Render will automatically redeploy

## Step 3: Verify It Works!

1. Wait for deployment to complete
2. Go to your app URL
3. Change an organization's status
4. Check Render logs - you should see: "Successfully saved to Supabase (status 200)"
5. Refresh the page - status should still be there! 🎉

## Troubleshooting

**If you see "Supabase PATCH failed":**
- Make sure you ran the SQL in Step 1
- Check the error message in logs
- Verify env vars are spelled correctly (no typos, no extra spaces)

**If changes don't persist:**
- Check Render logs for error messages
- In Supabase Table Editor, check if `state_data` is updating

**If you want to disable Supabase (use local file):**
- Simply delete the 3 env vars from Render
- App will automatically use `state.json` file

