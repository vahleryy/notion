# iPhone Photo Sorter (Shortcuts)

Two shortcuts:

- **Sort My Photos**: reviews recent photos, videos and screenshots one at a time. Each item gets filed into an album, queued for Google Photos, deleted, or skipped.
- **Clear Backed Up**: deletes everything in the "To Google Photos" album *after* you've confirmed it's in Google Photos.

Apple no longer lets you import shortcut files from outside, so you build these by hand in the Shortcuts app. It takes about 15 minutes.

---

## Step 0: Create albums (Photos app)

Open Photos, then Albums, then **+**, then New Album, and create:

| Album | Purpose |
|---|---|
| Therapy | Psychology / therapy videos (kept on phone) |
| Cooking | Recipes, cooking tips |
| To Buy | Things to buy |
| Tips | General tips |
| To Google Photos | Memories to back up, then delete |
| Reviewed | Keep on phone, no category (stops it showing up again) |

You can rename or add categories. Just keep the album names and menu names matching.

---

## Shortcut 1: Sort My Photos

Open the Shortcuts app, tap **+**, and name it **Sort My Photos**. Add these actions in order (search for each name in the action search bar):

1. **Find Photos**
   - Tap "Add Filter" and set it to **All of the following are true**:
     - `Date Taken` `is in the last` `30 days`
     - `Album` `is not` `Therapy`
     - `Album` `is not` `Cooking`
     - `Album` `is not` `To Buy`
     - `Album` `is not` `Tips`
     - `Album` `is not` `To Google Photos`
     - `Album` `is not` `Reviewed`
   - Sort by: `Date Taken`, Order: `Oldest First`
   - Limit: **on**, `25` (one sitting's worth; run again for more)

2. **Repeat with Each** (item in Photos)

   Inside the repeat:

   3. **Quick Look**, set to `Repeat Item`. This shows the photo full screen (videos play). Tap **Done** to continue.

   4. **Choose from Menu**, prompt: `File this where?` Add these options:
      `Therapy` · `Cooking` · `To Buy` · `Tips` · `Google Photos` · `Keep` · `Delete` · `Skip`

      Under each option add:

      | Option | Action inside it |
      |---|---|
      | Therapy | **Add to Album**: `Repeat Item` to `Therapy` |
      | Cooking | **Add to Album**: `Repeat Item` to `Cooking` |
      | To Buy | **Add to Album**: `Repeat Item` to `To Buy` |
      | Tips | **Add to Album**: `Repeat Item` to `Tips` |
      | Google Photos | **Add to Album**: `Repeat Item` to `To Google Photos` |
      | Keep | **Add to Album**: `Repeat Item` to `Reviewed` |
      | Delete | **Add to Variable**: `Repeat Item` to variable named `ToDelete` |
      | Skip | *(leave empty; it will show up again next time)* |

5. After **End Repeat**, add **If** `ToDelete` `has any value`.
   - Inside the If: **Delete Photos**, set to `ToDelete`
   - (Leave Otherwise empty.)

That's it. When you run it:

1. An item appears full screen. Tap **Done**.
2. Pick from the menu (1 tap).
3. Repeat for up to 25 items.
4. At the end iOS asks **once** to confirm deleting everything you marked. Deleted items go to Recently Deleted for 30 days.

> Tip: to quit early, swipe the shortcut away or tap the stop button. Items marked "Delete" in that session won't be deleted, but they'll show up again next time.

---

## Shortcut 2: Clear Backed Up

Run this only **after** you've uploaded the "To Google Photos" album to Google Photos and checked the items are there.

1. **Find Photos**: filter `Album` `is` `To Google Photos` (no limit)
2. **Show Alert**: `Delete these from iPhone? Make sure they're in Google Photos first.` (Show Cancel: on)
3. **Delete Photos**: `Photos`

### Getting them into Google Photos

- **Backup on:** Google Photos uploads everything automatically. Open the Google Photos app and let it finish (check the profile icon for "Backup complete"), then sort into your Google albums there.
- **Backup off:** in the Photos app, open the "To Google Photos" album, tap Select, select all, tap Share, then choose Google Photos (or open Google Photos and upload from that album).

Deleting from iPhone does **not** delete from Google Photos once it's backed up.

---

## Make it a habit

- **Home Screen:** in Shortcuts, long-press Sort My Photos, then Share, then **Add to Home Screen**.
- **Weekly reminder:** go to Shortcuts, then Automation, then **+**, then Time of Day (e.g. Sunday 7pm, Weekly), and choose **Run After Confirmation** with **Sort My Photos**. You'll get a notification to tap.

## Good to know

- **Deleting a photo from iPhone removes it from every album.** Albums are just labels on the same file. Anything you want off the phone must be in Google Photos first.
- Want another category? Create the album, add an `Album is not ...` filter in step 1, and add a menu option with an **Add to Album** action.
- To review older items, change `30 days` in step 1 to e.g. `365 days`.
