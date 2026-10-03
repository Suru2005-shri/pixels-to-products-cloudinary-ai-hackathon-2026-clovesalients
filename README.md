# pixels-to-products-cloudinary-ai-hackathon-2026-clovesalients
Hackathon team repository for Clovesalients - [hackindia-team:pixels-to-products-cloudinary-ai-hackathon-2026:clovesalients]
YatraLens — AI media pipeline for foreigners visiting India
Hackathon: HackIndia · PS-01 Track 1 · AI Media Pipelines (Cloudinary AI Skills Pack)
Problem: Foreign travellers take hundreds of photos of unfamiliar food, signs, monuments and transport. They can't organise them, don't know local etiquette, and have no easy way to share polished memories.
Solution: Upload a photo → Cloudinary AI tags it, moderates it, we classify it into a travel category with India-specific tips, store structured metadata, and let you search and generate postcards.
Pipeline → Cloudinary capabilities
Stage
What happens
Cloudinary feature
Ingest
Photo uploaded into yatralens/<trip>
Upload API
Analyse
Objects/scenes tagged (≥0.6 confidence)
Auto-tagging (categorization, auto_tagging)
Safety
Unsafe images rejected & deleted
Moderation (aws_rek)
Organise
Category, city, trip, traveler saved
Structured metadata (context)
Find
Search by tag/city/category
Search API
Present
Square AI-cropped thumbs
Content-aware crop (c_fill,g_auto)
Share
Postcard with border + text; cutout postcard
Background removal, overlays, transformations
Deliver
Fast, small, right format
f_auto, q_auto, dpr_auto
Run
npm install
cp .env.example .env     # add Cloudinary keys (optional: runs in demo mode without)
npm start                # http://localhost:3000
Without keys it runs in demo mode (in-memory, filename-based fake tags) so the UI can be tried offline.
API
POST /api/upload (multipart: photo, city, trip, traveler, country)
GET /api/photos?q=&category=&city=&trip=
GET /api/postcard?id=&city=&message=&style=classic|cutout
GET /api/summary?trip=
GET /api/status
Notes
Enable the Google Auto Tagging and AWS Rekognition Moderation add-ons in your Cloudinary console, or change TAGGING_ADDON / MODERATION_ADDON.
Extend ideas: video clips (resource_type: video, q_auto, f_auto), multilingual sign translation, scam-alert tips per city.
