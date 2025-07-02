# 🎧 Sonarr & Radarr: Custom Formats for English Dubbed / Dual Audio Anime

This repository provides a set of **Custom Formats (CFs)** for use with **Sonarr** and **Radarr** to automatically prioritize **English Dubbed** media releases. The goal is to avoid subtitle-only or original-language-only content by scoring releases with terms like:

- `Dual Audio`
- `Eng Dub`
- `Dubbed`
- `English Audio`

## 📌 Why This Exists

By default, Sonarr and Radarr may fetch content in any language depending on what's available. If you're specifically looking for **English dubbed anime** (especially to avoid reading subs all the time), these JSON-based Custom Formats let you take full control of what's downloaded.

## 🧠 How It Works

Custom Formats use **Release Title matching** and **Language metadata scoring** to:

- ✅ Prioritize dubbed content using positive scores
- ❌ Penalize sub-only or original-language-only content with reverse scoring (e.g., -10000)
- 🎯 Work in both Radarr (with language = Any) and Sonarr (which lacks language selection in profiles)

---

## 📁 Included Custom Formats

| Format Name                 | Description                                                        | Score     |
|----------------------------|--------------------------------------------------------------------|-----------|
| `Language: English Dubbed` | Matches `Dual Audio`, `Eng Dub`, `Dubbed`, or `English` tags       | `+100`    |
| `Language: Not English`    | Penalizes any non-English release based on metadata                | `-10000`  |
| `Language: Original Japanese` _(optional)_ | Penalizes Japanese-only releases to avoid sub-only content | `-10000`  |

> You can stack this with your quality preferences (`x265`, `1080p`, etc.) for even more control.

---

## 📥 How to Import Custom Formats

### 1. Open Radarr or Sonarr in your browser

- Go to: `Settings` → `Custom Formats`

### 2. Import the JSON

#### Option A: Manual Import

1. Click **"Add New"**
2. Copy fields from the JSON:
   - **Name**
   - **Specifications**:
     - `ReleaseTitleSpecification` (regex match for terms like `Eng Dub`)
     - `LanguageSpecification` (language ID, e.g., `1` = English)
   - **Score** (added later in the profile)

#### Option B: Trash-Guides ID Import (if available)

1. Click **"Import"**
2. Paste the `trash_id` (e.g., `0dc8aec3bd1c47cd6c40c46ecd27e846`)
3. Radarr/Sonarr may auto-fill the format

---

## 📌 Apply in Your Quality Profile

1. Go to `Settings` → `Profiles`
2. Copy and Edit your profile (e.g., `HD-1080p`)
3. Under **Custom Formats**, click ➕ and select the imported formats
4. Assign the following scores:

| Custom Format               | Score     |
|----------------------------|-----------|
| Language: English Dubbed   | `+100`    |
| Language: Not English      | `-10000`  |

5. **Radarr only**: Set `Preferred Language` to `Any` in the profile

---

## 🧪 Test It

To verify it works:

- Go to a show/movie
- Click 🔍 **Manual Search**
- You should see English Dubbed releases rise to the top
- Sub-only/original-language releases should be de-prioritized or blocked

---

## 🧰 Language Codes for Reference (Used in LanguageSpecification)

| Language     | Code |
|--------------|------|
| English      | 1    |
| Japanese     | 2    |
| German       | 4    |
| Dutch        | 7    |
| Flemish      | 19   |
| Original     | -2   |

---

## 📚 Resources

- [TrashGuides: Language Custom Formats](https://trash-guides.info/Radarr/Radarr-collection-of-custom-formats/#language-custom-formats)
- [Sonarr Documentation](https://sonarr.tv/)
- [Radarr Documentation](https://radarr.video/)

---

## 💬 About

Created by **Whsikey** 
If you're a recruiter or collaborator interested in automation, LLMs, or media infrastructure tooling, feel free to reach out.
---
