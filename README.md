# Polar webhooks

This is a simple webhook plugin for Polar Anticheat. You can configure everything.

## Config
```yml
webhook_url: "https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz"
# Placeholders
# Mitigation: %PLAYER_NAME%, %VL%, %CHECK_TYPE%, %CHECK_NAME%, %DETAILS%
# Detection: %PLAYER_NAME%, %VL%, %CHECK_TYPE%, %CHECK_NAME%, %DETAILS%
# Cloud Detection: %PLAYER_NAME%, %CHECK_TYPE%, %DETAILS%
# Punishment: %PLAYER_NAME%, %PUNISHMENT%, %REASON%
mitigation:
  webhook_url: "https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz"
  enabled: true
  cooldown_per_player_and_type: 5 # Seconds
  notifications:
    - 'MOVEMENT'
    - 'VELOCITY'
    - 'GROUND_SPOOF'
    - 'LATENCY_ABUSE'
    - 'TICK_SPEED'
    - 'REACH'
    - 'BLOCK_INTERACT'
    - 'PHASE'
    - 'CLOUD'
  filter_detail_lines: # Allows you to filter out certain detail lines from being sent to Discord
    - 'Click to teleport'
    - 'Debug*' # Line starting with "Debug" will be filtered out
  content: 'Player %PLAYER_NAME% was mitigated for %VL% violations of %CHECK_TYPE% - %CHECK_NAME%'
  embed:
    title: 'Polar - Mitigation'
    description: ''
    color: 'ff0000' # Hex color code
    footer:
      text: 'Polar Webhooks by Shorty'
      icon_url: ''
    thumbnail:
      url: 'https://mc-heads.net/avatar/%PLAYER_NAME%'
    image:
      url: ''
    fields:
      0:
        name: 'Player'
        value: '%PLAYER_NAME%'
        inline: true
      1:
        name: 'Check'
        value: '%CHECK_TYPE% - %CHECK_NAME%'
        inline: true
      2:
        name: 'Details'
        value: '%DETAILS%'
        inline: false
detection:
  webhook_url: "https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz"
  enabled: true
  cooldown_per_player_and_type: 0 # Seconds
  notifications:
    - 'MOVEMENT'
    - 'VELOCITY'
    - 'GROUND_SPOOF'
    - 'LATENCY_ABUSE'
    - 'TICK_SPEED'
    - 'REACH'
    - 'BLOCK_INTERACT'
    - 'PHASE'
    - 'CLOUD'
  filter_detail_lines: # Allows you to filter out certain detail lines from being sent to Discord
    - 'Click to teleport'
    - 'Debug*' # Line starting with "Debug" will be filtered out
  content: 'Player %PLAYER_NAME% detected for %CHECK_TYPE% - %CHECK_NAME%'
  embed:
    title: 'Polar - Detection'
    description: 'Player %PLAYER_NAME% detected for %CHECK_TYPE% - %CHECK_NAME%'
    color: 'ff0000' # Hex color code
    footer:
      text: 'Polar Webhooks by Shorty'
      icon_url: ''
    thumbnail:
      url: 'https://mc-heads.net/avatar/%PLAYER_NAME%'
    image:
      url: ''
    fields:
      0:
        name: 'Player'
        value: '%PLAYER_NAME%'
        inline: true
      1:
        name: 'Check'
        value: '%CHECK_TYPE% - %CHECK_NAME%'
        inline: true
      2:
        name: 'Details'
        value: '%DETAILS%'
        inline: false
cloud_detection: # Please note that %VL% and %CHECK_NAME% are not available for cloud detections
  webhook_url: "https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz"
  enabled: true
  cooldown_per_player_and_type: 0 # Seconds
  notifications:
    - 'AUTO_CLICKER'
    - 'CHEST_STEALER'
    - 'COMBAT_BEHAVIOR'
    - 'INVALID_PROTOCOL'
    - 'SCAFFOLD'
    - 'CPS_LIMIT'
    - 'RIGHT_CPS_LIMIT'
  filter_detail_lines: # Allows you to filter out certain detail lines from being sent to Discord
    - 'Click to teleport'
    - 'Debug*' # Line starting with "Debug" will be filtered out
  content: '[Cloud] Player %PLAYER_NAME% detected for %CHECK_TYPE%'
  embed:
    title: 'Polar - Detection'
    description: 'Player %PLAYER_NAME% detected for %CHECK_TYPE%'
    color: 'ff0000' # Hex color code
    footer:
      text: 'Polar Webhooks by Shorty'
      icon_url: ''
    thumbnail:
      url: 'https://mc-heads.net/avatar/%PLAYER_NAME%'
    image:
      url: ''
    fields:
      0:
        name: 'Player'
        value: '%PLAYER_NAME%'
        inline: true
      1:
        name: 'Check'
        value: '%CHECK_TYPE% - %CHECK_NAME%'
        inline: true
      2:
        name: 'Details'
        value: '%DETAILS%'
        inline: false
punishment: # Please note that no other placeholders except for %PLAYER_NAME%, %PUNISHMENT% and %REASON% are available for punishments
  webhook_url: "https://discord.com/api/webhooks/1234567890/abcdefghijklmnopqrstuvwxyz"
  enabled: true
  types_enabled: # Remove from list to disable notifications for that punishment type
    - 'BAN'
    - 'KICK'
  cooldown_per_player: 0 # Seconds
  content: 'Player %PLAYER_NAME% was punished for %REASON% (%PUNISHMENT%)'
  embed:
    title: 'Polar - Punishment'
    description: ''
    color: 'ff0000' # Hex color code
    footer:
      text: 'Polar Webhooks by Shorty'
      icon_url: ''
    thumbnail:
      url: 'https://mc-heads.net/avatar/%PLAYER_NAME%'
    image:
      url: ''
    fields:
      0:
        name: 'Player'
        value: '%PLAYER_NAME%'
        inline: true
```