proxies:
- name: 🇫🇷 Франция ⚡1
  type: vless
  server: 45.12.133.214
  port: 443
  uuid: 2a29404d-fe4b-4a06-8f04-90abb0f00989
  network: tcp
  tls: true

- name: 🇫🇷 Франция ⚡2
  type: vless
  server: 45.12.133.214
  port: 4443
  uuid: 2a29404d-fe4b-4a06-8f04-90abb0f00989
  network: tcp
  tls: true

- name: 🇫🇷 Франция ⚡3
  type: vless
  server: 45.12.133.214
  port: 8443
  uuid: 2a29404d-fe4b-4a06-8f04-90abb0f00989
  network: tcp
  tls: true

proxy-groups:
- name: 🚀 AUTO
  type: url-test
  url: http://www.google.com/generate_204
  interval: 300
  proxies:
  - 🇫🇷 Франция ⚡1
  - 🇫🇷 Франция ⚡2
  - 🇫🇷 Франция ⚡3

rules:
- MATCH,🚀 AUTO
