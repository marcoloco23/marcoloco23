# Metrics Configuration Reference

## Quick Configuration Guide

This file contains common configuration snippets for easy copy-paste into the metrics workflow.

## 🎯 Plugin Quick-Add Configurations

### Activity Plugin (Recent GitHub Activity)
```yaml
# === PLUGIN: ACTIVITY ===
# Shows recent GitHub activity feed
plugin_activity: yes
plugin_activity_limit: 10
plugin_activity_load: 300
plugin_activity_days: 14
plugin_activity_filter: all
plugin_activity_visibility: all
plugin_activity_timestamps: yes
```

### Repositories Plugin (Featured Repositories)
```yaml
# === PLUGIN: REPOSITORIES ===
# Showcases featured repositories
plugin_repositories: yes
plugin_repositories_featured: marcoloco23/Ted, marcoloco23/midiGPT
plugin_repositories_order: featured, pinned, starred, random
plugin_repositories_forks: yes
plugin_repositories_affiliations: owner, collaborator
```

### Lines Plugin (Code Statistics)
```yaml
# === PLUGIN: LINES ===
# Lines of code statistics
plugin_lines: yes
plugin_lines_history_limit: 1
plugin_lines_repositories_limit: 4
plugin_lines_sections: base, repositories, history
```

### WakaTime Plugin (Coding Time Tracking)
```yaml
# === PLUGIN: WAKATIME ===
# Detailed coding time analytics
plugin_wakatime: yes
plugin_wakatime_token: ${{ secrets.WAKATIME_TOKEN }}
plugin_wakatime_days: 30
plugin_wakatime_sections: time, projects, projects-graphs, languages, languages-graphs, editors, os
plugin_wakatime_limit: 5
plugin_wakatime_url: https://wakatime.com
plugin_wakatime_user: current
```

### Music Plugin (Spotify/Last.fm)
```yaml
# === PLUGIN: MUSIC ===
# Music listening activity
plugin_music: yes
plugin_music_provider: spotify  # or lastfm
plugin_music_token: ${{ secrets.SPOTIFY_TOKEN }}
plugin_music_limit: 4
plugin_music_played_at: yes
plugin_music_top_type: tracks
plugin_music_mode: top
plugin_music_time_range: short_term
```

### Posts Plugin (Blog Integration)
```yaml
# === PLUGIN: POSTS ===
# Blog posts and articles
plugin_posts: yes
plugin_posts_source: dev.to  # or medium, hashnode, etc.
plugin_posts_descriptions: yes
plugin_posts_covers: yes
plugin_posts_limit: 4
plugin_posts_user: marcoloco23
```

### Stack Overflow Plugin
```yaml
# === PLUGIN: STACKOVERFLOW ===
# Stack Overflow activity
plugin_stackoverflow: yes
plugin_stackoverflow_user: YOUR_SO_USER_ID
plugin_stackoverflow_sections: answers-top, questions-recent
plugin_stackoverflow_limit: 2
plugin_stackoverflow_lines: 4
plugin_stackoverflow_lines_snippet: 2
```

### Traffic Plugin (Repository Analytics)
```yaml
# === PLUGIN: TRAFFIC ===
# Repository traffic statistics
plugin_traffic: yes
plugin_traffic_skipped: ""
```

## 🎨 Template Configurations

### Terminal Template
```yaml
template: terminal
config_twemoji: yes
config_gemoji: yes
config_octicon: yes
```

### Repository Template
```yaml
template: repository
repo: marcoloco23/marcoloco23
```

### Markdown Template
```yaml
template: markdown
config_output: TEMPLATE.md
markdown: TEMPLATE.md
markdown_cache: .cache
```

## 🔧 Advanced Base Configurations

### Enhanced Base Configuration
```yaml
base: header, activity, community, repositories, metadata
base_indepth: yes
base_hireable: yes
base_skip: yes
repositories_forks: yes
repositories_affiliations: owner, collaborator, organization_member
repositories_batch: 5
```

### Performance Optimizations
```yaml
# Optimize for faster execution
repositories_batch: 10
plugin_languages_analysis_timeout: 15
plugin_habits_from: 500
config_presets: "@marcoloco23"
optimize: css, xml, svg
```

## 🌍 Localization Options

### Timezone Settings
```yaml
config_timezone: America/New_York        # Eastern Time
# config_timezone: America/Los_Angeles   # Pacific Time
# config_timezone: Europe/London         # GMT
# config_timezone: Asia/Tokyo            # JST
```

### Language Settings
```yaml
config_locale: en                        # English
# config_locale: es                      # Spanish
# config_locale: fr                      # French
# config_locale: de                      # German
```

## 📊 Output Customizations

### Multiple Output Formats
```yaml
# Generate multiple formats
config_output: github-metrics.svg
config_display: large
config_animations: yes
config_base64: no
config_padding: 0, 8 + 11%
```

### Custom Styling
```yaml
# Custom colors and styling
config_order: base.header, base.activity+community, languages, notable
config_twemoji: yes
config_gemoji: yes
config_octicon: yes
config_display: large
config_animations: yes
```

## 🔐 Security & Privacy

### Privacy Settings
```yaml
# Limit private information exposure
repositories_affiliations: owner, collaborator
plugin_achievements_secrets: no
plugin_notable_repositories: no
base_hireable: no
```

### Rate Limiting
```yaml
# Optimize API usage
repositories_batch: 5
plugin_languages_analysis_timeout: 30
delay: 120  # 2-minute delay between requests
```

## 📝 Conditional Configurations

### Environment-Based Settings
```yaml
# Use different settings for different branches/environments
user: ${{ github.repository_owner }}
committer_branch: ${{ github.ref_name }}
committer_message: "Update metrics"
```

## 🚀 Quick Setup Commands

### Add New Plugin (Example: Activity)
1. Copy the activity plugin configuration above
2. Add to `.github/workflows/metrics.yml` in the appropriate section
3. Update `config_order` to include the new plugin
4. Add corresponding `![Activity](./activity.svg)` to README.md

### Enable Additional Features
1. **For WakaTime**: Create account at wakatime.com, get API key, add as `WAKATIME_TOKEN` secret
2. **For Music**: Connect Spotify/Last.fm, get API credentials, add as secrets
3. **For Google Maps**: Get Google Maps API key, add as `GOOGLE_MAP_TOKEN` secret

### Testing New Configurations
1. Make changes to workflow file
2. Commit and push changes
3. Go to Actions tab → Metrics workflow → Run workflow
4. Check generated SVG files
5. Update README.md if needed

---

*Configuration reference for lowlighter/metrics v3.34+*
