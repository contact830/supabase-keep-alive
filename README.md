name: Keep Supabase Alive

on:
  schedule:
    - cron: '0 0 * * 0,3'  # Runs dimanche et mercredi à minuit UTC
  workflow_dispatch:  # Permet de lancer manuellement

jobs:
  ping-supabase:
    runs-on: ubuntu-latest
    
    steps:
      - name: Ping Supabase Database
        run: |
          curl -X GET "[https://nvtzgbccosmivsvbdlmo.supabase.co/rest/v1/" \
            -H "apikey: ${{ secrets.SUPABASE_KEY }}" \
            -H "Authorization: Bearer ${{ secrets.SUPABASE_KEY }}"
