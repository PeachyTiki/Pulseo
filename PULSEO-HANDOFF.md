# PULSEO FITNESS APP — HANDOFF DOCUMENT
## For continuing development in a new conversation

**Creator:** PeachyTiki (Monteo Pietsch)
**Current Version:** v2.0 (v6 backup format)
**File:** Single HTML file (549KB), ZIP for WebIntoApp APK

---

## ARCHITECTURE
- Single HTML file: `<style>` CSS + `<body>` HTML + `<script>` JS
- All data in localStorage
- 5 tabs: Habits, Workout, Nutrition, Body, Settings
- 4 visual modes: Normal Dark/Light + Retro Dark/Light
- PWA-capable, runs as APK via WebIntoApp.com

## STORAGE KEYS
| Key | Type | Content |
|---|---|---|
| g_hl | JSON array | Habit list definitions |
| g_hd | JSON object | Habit data per day {date: {id: value}} |
| g_wl | JSON array | Workout plans |
| g_wlog | JSON object | Weight logs from live workouts |
| g_body | JSON object | Body stats per day {date: {weight, bf, photo}} |
| g_meals | JSON object | Meal logs per day {date: [{n,wt,cal,p,c,f,fb,t}]} |
| g_cfoods | JSON array | Custom foods (per 100g) |
| g_ngoals | JSON object | Nutrition goals {cal:[min,max], p, c, f, fb} |
| g_ncalc | JSON object | Calculator params {wGoal, mGoal, auto} |
| g_ntrack | JSON array | Which nutrients to track ['cal','p','c','f','fb'] |
| g_bday | string | Birthday (YYYY-MM-DD) |
| g_height | number | Height in cm |
| g_bunit | JSON object | Units {w:'kg'/'lb', h:'cm'/'in'} |
| g_gender | string | 'm' or 'f' |
| g_btype | string | 'ecto'/'meso'/'endo' |
| g_theme | string | 'dark' or 'light' |
| g_lang | string | Language code (en/es/fr/de/ru/zh/ja/hi/pt/ar/bn) |
| g_notif | JSON object | Notification settings |
| g_retro | boolean | Retro mode on/off |
| g_mdog | boolean | Muscle Dog unlocked |
| g_mdog_off | boolean | Muscle Dog toggled off |
| g_kj | boolean | Show kilojoules instead of kcal |
| g_lb | string | Last backup date |
| g_body_setup | boolean | Body onboarding shown |

## BACKUP FORMAT (v6)
```json
{
  "habits": {}, "habitList": [], "workouts": [], "wlog": {},
  "body": {}, "birthday": "", "height": 0, "bunit": {},
  "gender": "", "btype": "", "kj": false,
  "meals": {}, "cfoods": [], "ngoals": {}, "ntrack": [], "ncalc": {},
  "settings": {
    "theme": "", "lang": "", "notif": {}, "retro": false,
    "mdog": false, "mdogOff": false
  },
  "v": 6
}
```

## EXERCISE DATA FORMAT
```json
{
  "n": "Bench Press", "s": 4, "r": "8-12", "m": "Chest",
  "w": 60, "rt": 90, "ert": 60, "bw": false
}
```
- w = weight in KG (always stored metric)
- rt = rest between SETS in seconds
- ert = rest between EXERCISES in seconds
- bw = bodyweight flag

## FOOD DATABASE
- 155 built-in foods (FOOD_DB array) with: n, cal, p, c, f, fb, cat per 100g
- Custom foods saved in g_cfoods with same format
- Categories: fruit, veg, protein, dairy, grain, legume, nut, fat, drink, snack, misc, meal, custom

## MUSCLE DOG EASTER EGG
- 5 hidden 🐕 emojis (one per tab: habits/workout/nutrition/body/settings)
- 6% opacity, 6px — nearly invisible
- Click all 5 → unlocks Muscle Dog
- 12 base64 PNG images embedded (6 normal + 6 retro variants)
- Images: normal, talk, grab, wise, nerd, fancy
- 101 quotes: 86 regular + 5 wise + 5 nerd + 5 fancy
- Walks/runs to random positions, 50% idle time
- Speech bubble attached to dog div
- Drag to pick up (grab image)
- Watchdog timer prevents permanent breaking
- Settings toggle appears after unlock

## 4 VISUAL MODES
- Normal Dark: --bg:#0A0A0F, --card:#12121A, rounded, modern
- Normal Light: --bg:#F5F5F7, --card:#FFF, rounded
- Retro Dark: --bg:#3A6EA5 (Vista blue), --card:#1E3F6E, square, outset borders
- Retro Light: --bg:#D4D0C8 (gray), --card:#ECE9D8, square, classic Windows
- Retro toggles turn GREEN (#44BB44) when on
- All retro CSS scoped under [data-retro]

## LIVE WORKOUT FLOW
1. Exercise screen (set counter + exercise timer)
2. "SET DONE ✓" → Rest between sets (timer, goes red over limit)
3. After last set → "END EXERCISE" → Weight input (if not bodyweight)
4. If ert > 0 → Rest between exercises screen (shows next exercise preview)
5. "START NEXT EXERCISE →" → Next exercise
6. After last exercise → Done screen → Save & Exit

## WHAT NEEDS TO BE BUILT NEXT
1. **Sub-habits** — habits can have child habits, nested display
2. **Drag-to-reorder habits** — touch drag handler, reorder in g_hl
3. **Habit color picker** — UI to change habit color
4. **Bidirectional nutrition ↔ habits** — nutrition habit auto-syncs with food tracker
5. **10,000 food database** — expand from 155 to 10K (consider IndexedDB or lazy-load)
6. **Exercise rest blocks in form** — visual separator between exercises showing rest config
7. **Rest between exercises in exercise form** — show as a block BETWEEN exercises, not inside them

## 11 LANGUAGES
en, es, fr, de, ru, zh, ja, hi, pt, ar, bn
- All have tab1-tab5 translations
- ~30 key strings per language

## KEY FUNCTIONS (80+)
sV, oM, cM, rH, tH, tCH, pD, sGF, tL, aHb, sNHb, eHb, sEHb, dHb, bG, gBr,
rW, bOV, bDay, cWk, togG, aWk, aEx, rExL, svWk, eWk, svEWk, dWk,
startLW, lwRender, lwCompleteSet, lwNextSet, lwEndEx, lwAdvanceEx, lwLogW, finishLW, closeLW,
openWT, renderWT, rB, saveBod, hPI, buildBodyGraph, miniLine, calcBMI, delPhoto, bodyOnboard, saveOnboard,
rN, oNMeal, nSearch, selFood, updFoodPreview, logFood, delMeal, addCustomFood, oNCalc, applyNCalc, oNManual, saveNManual,
calcTDEE, calcGoals, autoRecalcNutr, togNutrTrack,
hWI, hHI, dlTpl, dlHTpl, showInst, showHInst, dl, rS, tTh, togNotif, updNotif,
bk, exportAI, hRe, setupNotif, setLang, toDisp, fromDisp, fmtTime, fmtTimer,
stMin, sortW, calcAge, getBday, sBday, getHt, sHt, getBU, sBU, calcStreak, pR, cT,
getRestDays, dayLbl, hDone, togRetro,
fDog, togMDog, initMDog, mdSchedule, mdMove, mdQuote, mdGrab, mdDragMove, mdDrop, getDogImg, setDogImg

## WEBINTOAPP SETTINGS
- Enable localStorage ✓
- Disable Pull to Refresh ✓
- App name: Pulseo
- 512x512 icon needed
