# GitHub Metrics Documentation

This repository uses [lowlighter/metrics](https://github.com/lowlighter/metrics) to automatically generate comprehensive GitHub statistics and analytics.

## 📋 Table of Contents

- [Overview](#overview)
- [Current Configuration](#current-configuration)
- [Generated Files](#generated-files)
- [Setup & Requirements](#setup--requirements)
- [Customization Options](#customization-options)
- [Future Improvements](#future-improvements)
- [Troubleshooting](#troubleshooting)

## 🔍 Overview

The metrics system automatically generates visual representations of GitHub activity, including:
- Profile statistics and activity
- Contribution calendars and patterns
- Programming language breakdowns
- Community engagement metrics
- Repository analytics
- Coding habits analysis

**Update Schedule:** Daily at midnight UTC  
**Manual Trigger:** Available via GitHub Actions UI  
**Template:** Classic SVG format  

## ⚙️ Current Configuration

### Enabled Plugins

| Plugin | Description | Output File |
|--------|-------------|-------------|
| **Base** | Profile overview, activity, repositories | `base.svg` |
| **Isocalendar** | 3D isometric contribution calendar | `isocalendar.svg` |
| **Habits** | Coding patterns and schedule analysis | `habits.svg` |
| **Languages** | Programming languages breakdown | `languages.svg` |
| **Notable** | Significant contributions highlights | `notable.svg` |
| **Reactions** | Community engagement metrics | `reactions.svg` |
| **Stargazers** | Repository stargazer analytics | `stargazers.svg` |
| **Achievements** | GitHub achievements and badges | `achievements.svg` |
| **Calendar** | Enhanced contribution calendar | `calendar.svg` |

### Configuration Details

```yaml
# Core Settings
user: marcoloco23
template: classic
timezone: America/New_York
repositories: 1000 (all accessible repos)
batch_size: 5 (processing efficiency)

# Base Metrics
- Profile header with avatar and basic info
- Activity timeline and contribution stats
- Repository overview and metadata
- Community engagement metrics

# Advanced Features
- In-depth language analysis (30s timeout)
- Full-year contribution calendar
- Detailed coding habits (30-day analysis)
- Stargazer geographical distribution
- Achievement tracking with secrets
```

## 📁 Generated Files

The workflow automatically generates these SVG files in the repository root:

1. **`base.svg`** - Primary profile overview
2. **`isocalendar.svg`** - 3D contribution calendar
3. **`habits.svg`** - Coding patterns analysis
4. **`languages.svg`** - Programming languages stats
5. **`notable.svg`** - Notable contributions
6. **`reactions.svg`** - Community engagement
7. **`stargazers.svg`** - Repository stargazer data
8. **`achievements.svg`** - GitHub achievements
9. **`calendar.svg`** - Contribution calendar

## 🔧 Setup & Requirements

### Prerequisites

1. **GitHub Personal Access Token**
   - Go to: https://github.com/settings/tokens
   - Create token with scopes: `public_repo`, `read:user`, `read:org`
   - Add as repository secret: `METRICS_TOKEN`

2. **Optional: Google Maps Token** (for stargazer worldmap)
   - Get token from Google Cloud Console
   - Add as repository secret: `GOOGLE_MAP_TOKEN`

3. **Optional: Author Emails** (for commit attribution)
   - Add as repository secret: `AUTHOR_EMAILS`

### Repository Secrets Required

| Secret Name | Description | Required |
|-------------|-------------|----------|
| `METRICS_TOKEN` | GitHub Personal Access Token | ✅ Yes |
| `GOOGLE_MAP_TOKEN` | Google Maps API token | ❌ Optional |
| `AUTHOR_EMAILS` | Additional author emails | ❌ Optional |

## 🎨 Customization Options

### Available Templates

- **Classic** (current) - Traditional GitHub-style metrics
- **Terminal** - Terminal/console theme
- **Repository** - Repository-focused view
- **Markdown** - Markdown format output

### Additional Plugins Available

Based on [lowlighter/metrics documentation](https://github.com/lowlighter/metrics):

#### Core Plugins
- **Activity** - Recent GitHub activity feed
- **Repositories** - Featured repositories showcase
- **Lines** - Lines of code statistics
- **Traffic** - Repository traffic analytics

#### Social Plugins
- **Music** - Last.fm, Spotify music activity
- **Posts** - Blog posts and articles
- **RSS** - RSS feed integration
- **Stack Overflow** - Stack Overflow activity
- **WakaTime** - Coding time tracking
- **Steam** - Steam gaming activity

#### Community Plugins
- **Chess** - Chess.com statistics
- **Crypto** - Cryptocurrency portfolio
- **Stock** - Stock market tracking
- **Screenshot** - Website screenshots

## 🚀 Future Improvements

### High Priority
- [ ] Add **Activity plugin** for recent GitHub activity feed
- [ ] Enable **Repositories plugin** to showcase featured projects
- [ ] Add **Lines plugin** for code statistics
- [ ] Configure **Traffic plugin** for repository analytics

### Medium Priority
- [ ] Integrate **WakaTime** for detailed coding time tracking
- [ ] Add **Posts plugin** for blog/article integration
- [ ] Enable **Music plugin** for Spotify/Last.fm activity
- [ ] Add **Stack Overflow** plugin for technical contributions

### Low Priority
- [ ] Experiment with **Terminal template** for different aesthetic
- [ ] Add **Community plugins** (Chess, Crypto, etc.)
- [ ] Create **custom plugin configurations**
- [ ] Implement **multi-template generation**

### Configuration Enhancements
- [ ] Optimize plugin parameters for better performance
- [ ] Add more detailed language analysis
- [ ] Configure custom color schemes
- [ ] Add repository filtering options
- [ ] Implement conditional plugin loading

## 🔧 Advanced Configuration Examples

### Adding Activity Plugin
```yaml
plugin_activity: yes
plugin_activity_limit: 10
plugin_activity_load: 300
plugin_activity_days: 14
plugin_activity_filter: all
plugin_activity_visibility: all
plugin_activity_timestamps: yes
```

### Adding WakaTime Integration
```yaml
plugin_wakatime: yes
plugin_wakatime_token: ${{ secrets.WAKATIME_TOKEN }}
plugin_wakatime_days: 30
plugin_wakatime_sections: time, projects, projects-graphs, languages, languages-graphs, editors, os
plugin_wakatime_limit: 5
```

### Adding Music Plugin
```yaml
plugin_music: yes
plugin_music_provider: spotify
plugin_music_token: ${{ secrets.SPOTIFY_TOKEN }}
plugin_music_limit: 4
plugin_music_played_at: yes
plugin_music_top_type: tracks
```

## 🐛 Troubleshooting

### Common Issues

1. **Workflow fails with authentication error**
   - Check `METRICS_TOKEN` is correctly set in repository secrets
   - Verify token has required scopes: `public_repo`, `read:user`, `read:org`
   - Ensure token hasn't expired

2. **Some metrics don't appear**
   - Check if you have sufficient activity for the metric
   - Verify plugin configuration parameters
   - Review workflow logs for specific errors

3. **SVG files not updating**
   - Check workflow execution in Actions tab
   - Verify cron schedule is correct
   - Manually trigger workflow to test

4. **Performance issues**
   - Reduce `repositories` limit if needed
   - Increase `repositories_batch` size
   - Adjust plugin timeout values

### Debugging Steps

1. Check GitHub Actions logs
2. Verify all required secrets are set
3. Test with minimal configuration
4. Review lowlighter/metrics documentation
5. Check for API rate limiting

## 📚 Resources

- **Main Documentation:** https://github.com/lowlighter/metrics
- **Plugin Documentation:** https://github.com/lowlighter/metrics/blob/master/README.md#-plugins
- **Template Documentation:** https://github.com/lowlighter/metrics/blob/master/README.md#-templates
- **Configuration Examples:** https://github.com/lowlighter/metrics/tree/master/.github/workflows
- **Community Examples:** https://github.com/lowlighter/metrics/blob/master/source/templates/community/README.md

## 📝 Version History

- **v1.0** - Initial setup with basic plugins
- **v1.1** - Enhanced configuration with comprehensive documentation
- **v1.2** - Added achievements and calendar plugins

---

*Last updated: $(date)*  
*Maintained by: @marcoloco23*
