# Travel Planner Mini Program · 旅途有谱

A WeChat mini-program MVP for travelers who have booked flights and hotels but still need a practical daily itinerary.

## Product problem

Trip planning often becomes a fragmented mix of notes, map searches and booking reminders. This prototype turns selected attractions and a hotel location into a day-by-day plan with transport and reservation guidance.

## Product highlights

- Search and select attractions in Beijing and Shanghai
- Add places through WeChat's native map picker
- Assign places manually or generate a balanced schedule
- Sort each day's route from the hotel using distance estimates
- Show transport suggestions and reservation reminders
- Save itineraries locally, with pin and delete controls

## Product decisions

- **Map selection instead of address parsing:** avoids unreliable geocoding during MVP validation.
- **Local data first:** avoids collecting user accounts or travel records.
- **Transparent estimates:** transport and reservation guidance is clearly labelled.
- **Manual + automatic planning:** balances user control with planning speed.

## Privacy

- No personal WeChat AppID, map key, API key or account information is included.
- The public configuration uses WeChat's tourist AppID placeholder.
- Environment files, private configuration, build output and caches are excluded.
- Itineraries stay on the user's device.

## Source

The privacy-reviewed source is available as [travel-planner-miniapp-source.zip](./travel-planner-miniapp-source.zip). It was built with vibe coding; my focus was the product workflow, feature priorities, interaction design and MVP trade-offs.

## Tech

Taro 4 · React · TypeScript · Sass · WeChat Mini Program APIs

> This is a portfolio MVP. A live WeChat release requires a private AppID and completion of WeChat's review process.
