# User Journeys

## Overview

This document defines the core user journeys for AI-HUMAN-CONNECTION. Each journey is designed with privacy, consent, safety, and accessibility as first-class requirements. AI augments human decision-making; it never replaces user agency.

**Key Principle:** Users always maintain control. AI provides recommendations and safety guardrails, but humans make final decisions.

---

## Journey 1: Registration

### Goal
A new user creates an account securely, with clear data practices and minimal friction, ready to begin the platform experience.

### User Steps

1. **Landing Page / App Store**
   - User discovers platform through marketing, referral, or app store
   - Sees value proposition: "Find genuine connections powered by AI"
   - Taps "Sign Up" button

2. **Authentication Choice**
   - User selects preferred authentication method:
     - Email + password (most common)
     - Google SSO (convenience)
     - Apple ID (iOS users, privacy-preserving)
     - Phone number (international users, SMS verification)
   - User enters credentials

3. **Email/Phone Verification**
   - Verification code sent to email or SMS
   - User enters verification code
   - Account is activated

4. **Basic Profile Information**
   - User provides:
     - Full name
     - Birth date (for age verification)
     - Gender identity (self-identified, multiple choice options)
     - Location (city/region, not street address)
   - User confirms name, date of birth, and location

5. **Privacy & Terms Acceptance**
   - User reviews (with accessible, clear language):
     - Terms of Service
     - Privacy Policy (data practices, AI usage, data retention)
     - Safety Guidelines
   - User must explicitly check boxes:
     - "I agree to Terms of Service"
     - "I understand my data usage" (separate checkbox for AI training consent)
     - "I commit to respectful behavior"
   - User cannot proceed without checking all boxes

6. **Welcome & Next Steps**
   - User sees confirmation screen
   - Message: "Welcome! Let's create your profile."
   - Call-to-action: "Next: Set up your profile"
   - Option to exit and return later

### AI Involvement

- **Account security monitoring:** AI detects suspicious registration patterns (multiple accounts from same device/IP, automated registrations)
- **Age verification:** AI cross-checks birth date for platform minimum age (18+)
- **Location verification:** AI flags mismatches between location provided and device location
- **Fraud detection:** AI screens for known bad actors or compromised devices

### Human Decisions

- User chooses authentication method
- User provides personal information (name, birth date, gender, location)
- User reads and explicitly accepts terms, privacy policy, and safety guidelines
- User decides whether to proceed or exit

### Safety Checks

1. **Minimum age verification:** Must be 18+ (enforced at signup)
2. **Location validation:** Detect suspicious geographic patterns
3. **Device fingerprinting:** Identify and flag duplicate accounts from same device
4. **Bot detection:** Identify automated signup attempts
5. **Consent tracking:** Log explicit opt-in for AI usage, terms, and safety guidelines
6. **Data minimization:** Collect only essential information; no unnecessary data harvesting

### Success State

- User completes all required fields
- User explicitly accepts all terms and policies
- Account is created and verified
- User receives confirmation email/SMS
- User is logged in and directed to Profile Creation journey
- AI has baseline data (name, age, location, authentication method)

### Failure States

**User stops at any point:**
- Session timeout → User can restart registration with same email
- Closes app/browser → User can resume with same email within 24 hours
- Rejects terms → User cannot proceed; given option to review or exit
- Authentication fails → User gets retry option (3 attempts before account lockout for security)
- Age verification fails (under 18) → Registration denied with message: "Must be 18+ to use platform"

**System errors:**
- Verification email doesn't arrive → Resend option; support escalation
- Database connection fails → Graceful error; user can retry
- SMS delivery fails → Fall back to email verification

### Edge Cases

1. **Users without email/phone verification capability**
   - Provide alternative verification (security questions, manual review)
   - Allow account creation with limited features until verified

2. **International users with non-standard locations**
   - Accept varied location formats (coordinates, postal codes, regions)
   - Translate privacy policy into user's language

3. **Users with privacy concerns**
   - Provide "minimal data" option (no location beyond country, no device fingerprinting)
   - Allow location privacy setting: "Only show country" instead of city

4. **Users changing gender/location post-signup**
   - Allow updates in settings without re-verification
   - Log changes for transparency and safety auditing

5. **Account recovery after deletion**
   - User can view deleted account info within 30-day grace period
   - Permanent deletion after 30 days
   - Prevent re-registration with same email within 90 days (avoid abuse loops)

6. **Multiple accounts from same person**
   - Allow 1 active account per verified email
   - Flag and review duplicate accounts from same device
   - User can request exception (e.g., separate personal and professional accounts) with manual review

7. **Accessibility considerations**
   - Screen reader support for all form fields
   - High contrast mode support
   - Voice-based authentication option
   - Keyboard-only navigation
   - Clear error messages with suggestions for correction

8. **Minors attempting to register**
   - Detect age <18 early
   - Block registration with age-appropriate message
   - Suggest parent/guardian options (future feature)

---

## Journey 2: Profile Creation

### Goal
User creates a rich, authentic profile that enables AI to perform deep compatibility analysis. Profile represents true self, not curated persona.

### User Steps

1. **Profile Intro Screen**
   - User sees: "Tell us about yourself. Authenticity leads to better matches."
   - Progress indicator: "Step 1 of 5"
   - Option to skip any section (but warned: "Skipped sections reduce match quality")

2. **About You (Text Profile)**
   - User writes responses to prompts (not fill-in-the-blank):
     - "Who are you at your core?" (200-500 chars)
     - "What matters most to you in life?" (200-500 chars)
     - "What's your communication style?" (100-200 chars)
     - "What are you looking for right now?" (200-300 chars)
   - Writing guidance: "Avoid clichés. Be specific and authentic."
   - Real-time feedback: Character count, estimated read time
   - User can edit, preview, and save

3. **Personality & Values (Questionnaire)**
   - User responds to 20-30 questions covering:
     - Core values (autonomy, family, growth, security, adventure, etc.)
     - Personality traits (introversion/extroversion, openness, conscientiousness, agreeableness, neuroticism)
     - Life goals (career, family, travel, spirituality, etc.)
     - Relationship preferences (casual, serious, long-term, collaboration)
     - Communication preferences (direct/indirect, conflict resolution style)
   - Format: Multiple choice, slider scales, or ranking
   - Estimated time: 5-10 minutes
   - User can save and return later
   - Optional: "Why did you choose that?" open-text explanations

4. **Lifestyle & Interests**
   - User selects interests from predefined categories (not free text initially):
     - Activities: Sports, arts, music, reading, gaming, travel, cooking, fitness, etc.
     - Communities: Professional, hobby, cause-driven, social groups
     - Preferences: Smoking, drinking, dietary preferences (relevant for dating/friendship)
   - User can add up to 20 tags (or describe custom interests)
   - User ranks top 3-5 interests as "most important"
   - Question: "How important are shared interests to your matches?" (slider)

5. **Photos & Representation**
   - User uploads 1-5 photos:
     - Guidelines: "Clear, recent photos of you. Be authentic."
     - Photo checks: AI detects blurry photos, filtered faces, or potentially fake images
     - Diversity: Prompt for variety (face, full body, activity, etc.)
   - For each photo:
     - User provides context: "What's happening in this photo?" (optional)
     - AI checks: Offensive content, explicit material, privacy violations
   - Alternative: Users uncomfortable with photos can use avatar/illustration (with disclosure)
   - Accessibility: Alt text required for all photos (for screen readers)

6. **Preference & Compatibility Settings**
   - User specifies what they're looking for:
     - Age range (if dating/romance)
     - Location preferences (nearby, willing to relocate, remote)
     - Connection goals (friendship, dating, professional, community)
     - Deal-breakers (smoking, long-distance, etc.)
   - User sets visibility:
     - "Who can see my profile?" (Everyone, matches only, hidden)
     - "Show my age/location?" (Yes, hide, approximate only)
     - "Show my photos?" (Yes, hide, blur face)

7. **Safety & Verification**
   - User provides identity verification (if age 18-25 or other risk factors):
     - Photo of ID verification (secure, encrypted, not stored long-term)
     - AI cross-checks: Name and age match on profile
   - User completes "Safety Pledge": "I commit to respectful, safe interactions"
   - User can add emergency contact or safety contact info (optional)

8. **Review & Confirmation**
   - User sees complete profile preview
   - AI provides feedback: "Your profile is 85% complete. Suggestions: Add more detail to 'What matters most to you'"
   - User can edit any section or proceed
   - Confirmation: "Publish profile to platform?"
   - User makes final decision to publish

### AI Involvement

- **Photo analysis:**
  - Detect blurriness, filters, extreme angles
  - Flag potentially offensive or explicit content
  - Estimate authenticity score (helps filter fake profiles)
  - Alert user to low-quality photos: "This photo is blurry. Try a clearer one?"

- **Text analysis:**
  - Detect generic/copy-paste bios vs. authentic writing
  - Identify red flags in language (manipulative language, inappropriate content)
  - Suggest improvements: "More detail here could help matches understand you better"
  - NLP to extract personality traits and values from free text

- **Completeness scoring:**
  - Calculate profile completeness percentage (0-100%)
  - Recommend missing sections that improve match quality
  - Warn if profile is too generic: "Vague profiles get fewer quality matches"

- **Safety screening:**
  - Cross-reference name/age/location for consistency
  - Check against known bad actors or banned users
  - Identify potential catfishing patterns (inconsistent info, stock photos)
  - Detect attempts to solicit money or illegal activities in profile

- **Embedding generation:**
  - Generate multi-dimensional embedding based on all profile data
  - This embedding is used later for compatibility matching
  - Update embedding if user updates profile

### Human Decisions

- User chooses to fill out each section (optional, but warned about match quality)
- User writes authentic responses vs. generic/curated ones
- User selects photos that represent their true self
- User specifies preferences and deal-breakers
- User decides visibility settings (privacy controls)
- User chooses whether to do identity verification
- User publishes or continues editing

### Safety Checks

1. **Age verification:** Confirm user is 18+ (enforce if under 25)
2. **Photo screening:** Automated detection of explicit/offensive content
3. **Text screening:** Detect manipulative language, inappropriate contact info exposure
4. **Identity verification:** Optional but recommended for dating/romance contexts
5. **Profile authenticity:** AI flags suspicious patterns (stock photos, inconsistent info)
6. **Data minimization:** Don't collect sensitive info (SSN, financial info, passwords)
7. **GDPR/privacy compliance:** User controls what's collected and visible
8. **Bot detection:** Identify fake profiles and automated signups
9. **Moderation queue:** High-risk profiles flagged for human review
10. **Abuse prevention:** Block attempts to embed contact info (email, phone, social media)

### Success State

- User completes profile with rich, authentic information
- Profile is published and visible to potential matches
- AI has generated embeddings for matching
- User receives confirmation: "Profile is live! Start discovering connections."
- User is prompted to proceed to Connection Intent Selection
- Profile appears in recommendation engines for matching users

### Failure States

**User stops at any point:**
- Session timeout → Profile saved as draft; user can resume
- Closes app → Draft saved; user prompted to resume on next login
- Skips all sections → Profile published as minimal; user warned about match quality
- Fails identity verification → Profile not published; user can retry or proceed without verification (with warning)
- AI flags profile as inauthentic → Profile held for manual review; user notified
- User deletes profile → All data deleted per retention policy (30-day grace period)

**System errors:**
- Photo upload fails → User can retry; alternate upload methods offered
- Text too long → System truncates with user confirmation
- API failures → Graceful degradation; save draft and retry later

### Edge Cases

1. **Users with privacy concerns**
   - Allow "private" profile mode (profile hidden until matched)
   - Option to blur or hide photos until mutual interest
   - Minimal data collection setting

2. **Users uncomfortable with photos**
   - Allow avatar/illustration instead of real photos
   - Clearly label as non-photo (transparency)
   - May affect match quality (disclosed to user)

3. **Users with multiple languages**
   - Allow profile in multiple languages
   - AI translates for cross-language matching
   - User chooses which language(s) their profile is discoverable in

4. **Neurodivergent or marginalized users**
   - Provide templates/examples for bio writing
   - Allow simple checkboxes instead of free text
   - Accessible language and instructions
   - Option to highlight marginalized identity if desired

5. **Users changing preferences later**
   - Allow full profile updates without re-verification
   - AI re-generates embeddings on update
   - Track changes for safety (detect dramatic shifts)

6. **Users with sensitive professions**
   - Allow profession obfuscation (e.g., "professional" instead of "doctor")
   - Hide location beyond regional level
   - Add photo privacy controls

7. **Accessibility for vision-impaired users**
   - Full screen reader support
   - Alternative text for all UI elements
   - Voice guidance through profile creation
   - Option to upload profile via voice recording

8. **International users**
   - Support non-Latin alphabets (Chinese, Arabic, Cyrillic, etc.)
   - Translate UI and guidance into user's language
   - Accept varied location formats
   - Account for cultural differences in what's appropriate to share

9. **Users with changing appearance**
   - Prompt annual photo updates
   - Detect significant photo/reality mismatch at first meeting (feedback loop)
   - Allow frequent photo updates without penalty

10. **Fraudulent or test accounts**
    - AI flags suspicious profile patterns for manual review
    - Moderation team can suspend or delete
    - User appeals process

---

## Journey 3: AI-Assisted Onboarding

### Goal
User completes guided onboarding that teaches platform features, establishes safety norms, and primes user for authentic connection. Onboarding is personalized to user's connection goals and learning style.

### User Steps

1. **Onboarding Welcome**
   - User sees personalized message based on profile:
     - "Welcome, Alex! Let's find you genuine connections."
   - Short video (60 seconds) on platform philosophy:
     - "We're not about volume. We're about finding people you genuinely connect with."
     - Show testimonial from previous user
   - Estimated onboarding time: "This takes ~10 minutes"
   - Option to skip entire onboarding (but recommended)

2. **Platform Overview**
   - User learns the 5-step connection flow (interactive tour):
     - Step 1: Complete your profile (done ✓)
     - Step 2: Choose connection type (coming next)
     - Step 3: AI finds compatible matches
     - Step 4: You decide who interests you
     - Step 5: Mutual connection & conversation
   - Visuals: Simple animations/diagrams showing flow
   - User can click "Learn More" on any step for details

3. **How AI Matching Works (Demystified)**
   - User learns what AI does (simple, jargon-free):
     - "AI analyzes your values, personality, and what you're looking for"
     - "AI looks for matches with genuine compatibility (not just hobbies)"
     - "AI explains WHY you're matched with someone"
     - "You always decide who to connect with. AI recommends; you choose."
   - User learns what AI doesn't do:
     - "AI never forces connections or contacts anyone on your behalf"
     - "AI never learns from you without consent"
     - "Your data is never sold to marketers"
   - Visual: Show sample match explanation (mock-up)
   - Transparency: "Learn about our AI ethics & bias audits" (link to docs)

4. **Safety & Respectful Community**
   - User learns community norms:
     - "Respect everyone's boundaries"
     - "No harassment, discrimination, or hateful language"
     - "Report concerns immediately"
     - "Everyone deserves to feel safe"
   - Real scenario walkthrough:
     - Scenario 1: "Someone messages you disrespectfully. [Report button] → [AI analysis] → [Swift moderation]"
     - Scenario 2: "You see concerning content from another user. [Flag] → [Review] → [Action taken]"
   - User must check: "I understand and commit to respectful behavior"

5. **Privacy & Your Data**
   - User learns privacy protections:
     - "Your profile is only visible to matches you're interested in"
     - "We use your data to improve matches, with your consent"
     - "You control what's visible (age, location, photos)"
     - "You can delete your account and all your data anytime"
   - Simple privacy visual: Show data flow (You → AI Matching Engine → Matches)
   - Highlight: "You're not the product. Our mission is your success, not engagement time."
   - User reviews privacy policy (summarized version, full version linked)

6. **Consent & Data Usage (Explicit Opt-In)**
   - User reviews how data is used:
     - **Required consent:**
       - Profile matching (required to use platform)
       - Safety monitoring (required)
     - **Optional consent:**
       - AI learning from your interactions (to improve matching)
       - Anonymous research on connection outcomes
       - Feedback survey participation
   - User explicitly checks boxes for optional consents (not auto-checked)
   - User can change consent anytime in settings
   - Impact displayed: "If you opt out of AI learning, matches may be less personalized"

7. **Interactive Feature Tour**
   - User walks through key features with guided interactions:
     - **Match Discovery:** "Here's how you'll see recommendations. Swipe to see explanations."
     - **Messaging:** "AI can help you start conversations confidently."
     - **Safety Tools:** "Here's how to report, block, or hide users."
     - **Settings:** "You control visibility, privacy, and preferences here."
   - Real screenshots/demo, not just text
   - User can actually try clicking through (no real actions taken)

8. **Connection Goals & Preferences (Quick Setting)**
   - User confirms connection goals:
     - "What type of connections are you looking for today?"
     - Options: Friendship, Dating, Professional Partnership, Community
     - Select up to 2 primary goals
   - Quick preference questions:
     - "How often do you want to hear from us?" (Daily digest, 3x/week, weekly, manual only)
     - "Preferred communication style?" (In-app notifications, email, SMS, push)
   - User saves preferences

9. **Next Steps & Momentum**
   - User sees encouraging message:
     - "You're all set! Time to discover connections."
   - Call-to-action: "Next: Choose your connection type" (Journey 4)
   - Optional: "Join our community" (link to blog, newsletter, community forum)
   - Progress indicator shows: "You're 30% through platform setup"

### AI Involvement

- **Personalized messaging:** AI customizes onboarding message and pace based on user profile
- **Content adaptation:** AI selects relevant scenarios/examples based on user's connection goals
- **Comprehension check:** AI can monitor if user is engaging or just clicking through (send back to key sections if not)
- **Recommendation:** AI suggests which features to prioritize based on user profile and goals
- **Follow-up:** AI sends post-onboarding reminder about key safety/privacy points after 1 day

### Human Decisions

- User chooses to skip, skim, or deeply engage with onboarding
- User reads and understands platform philosophy
- User makes informed consent decisions (optional data usage)
- User commits to safety and respectful behavior
- User confirms connection goals and preferences

### Safety Checks

1. **Consent tracking:** Log all explicit opt-ins and opt-outs
2. **Comprehension verification:** Ensure user understands safety norms before proceeding
3. **Red-flag detection:** If user behavior suggests they may violate community guidelines, flag for human review
4. **Clarity on expectations:** Ensure user understands AI's role and limitations
5. **Accessibility:** All onboarding content is accessible (captions, alt text, screen reader compatible)

### Success State

- User completes onboarding or explicitly chooses to skip
- User has read and accepted safety guidelines
- User has made informed consent decisions
- User understands AI matching and their role in deciding
- User has confirmed connection goals and preferences
- User sees confirmation: "Onboarding complete! Ready to find connections."
- User is ready to proceed to Connection Intent Selection (Journey 4)

### Failure States

**User stops at any point:**
- Session timeout → Onboarding saved; user can resume
- Closes app → User prompted to resume on next login
- Skips onboarding entirely → User can access onboarding anytime in settings
- Fails safety/consent check → Cannot proceed; must re-read and confirm
- Doesn't understand AI → Chat bot offers explanation, or live support

**System errors:**
- Video won't load → Text-only version offered
- Animations lag → Simplified version offered for low-bandwidth users

### Edge Cases

1. **Users who already used similar platforms**
   - Detect in profile/survey; offer "quick onboarding" (5 min vs. 15 min)
   - Highlight unique features vs. competitors
   - Focus on differences in approach (quality, consent, safety)

2. **Non-English speakers**
   - Provide full onboarding in user's language
   - High-quality translations (not auto-generated)
   - Voice-over options for key concepts

3. **Users with cognitive accessibility needs**
   - Offer simple version with fewer concepts
   - Longer, clearer explanations
   - Frequent breaks and checkpoints
   - Simplified visuals
   - Option for live support

4. **Users skipping onboarding**
   - Allow, but show prompt on first action: "Need help? Review our quick guide [link]"
   - Gentle reminder after 5 days of no connections formed: "Not sure where to start? Here's a refresher"
   - Proactive: If user takes actions that suggest confusion, suggest relevant onboarding sections

5. **Users in high-risk demographics**
   - Additional safety emphasis for younger users
   - For marginalized users, additional privacy controls highlighted
   - For first-time online daters, extra guidance on safety meeting practices

6. **Users with previous complaints/reports**
   - Returning users flagged as having violated guidelines see extended safety section
   - Review community norms before proceeding
   - Acknowledging and acceptance required

7. **Accessibility for vision-impaired users**
   - Full screen reader narration of all onboarding content
   - Audio descriptions of videos
   - Voice-guided tour option
   - High contrast text and large fonts

---

## Journey 4: Connection Intent Selection

### Goal
User explicitly chooses what type of connections they're seeking (friendship, dating, professional, community), establishing clear intent and matching context. This drives AI recommendation logic and user expectations.

### User Steps

1. **Connection Intent Landing Screen**
   - User sees clear, friendly message:
     - "What kind of connections are you looking for?"
     - Subtitle: "Be honest—there's no wrong answer. You can always change this later."
   - Visual: 4 large cards representing connection types
   - Progress indicator: "Step 1 of X" (if multi-step setup continues)

2. **Select Primary Connection Intent**
   - User sees 4 main options (each is a card/button):

   **Option A: Friendship**
   - Icon: Two people smiling
   - Description: "Find genuine friends who share your values and interests"
   - Examples: "Book club buddies, adventure companions, emotional support network"
   - Question: "Are you looking for local friends, online friends, or both?"
   - Sub-choices: Local, Online, Both
   - Additional info: "Friendship matches use shared interests + values + communication style"

   **Option B: Dating & Romance**
   - Icon: Heart
   - Description: "Find romantic partners and potentially long-term relationships"
   - Examples: "Looking for serious relationship, casual dating, open to either"
   - Question: "What are you looking for romantically?"
   - Sub-choices: Serious relationship, Casual dating, Open to either, Long-term partnership, Something else
   - Additional info: "Dating matches consider values, life goals, communication style, and chemistry"

   **Option C: Professional Partnership**
   - Icon: Briefcase/handshake
   - Description: "Find collaborators, mentors, co-founders, or professional connections"
   - Examples: "Co-founder, business partner, mentor, advisor, peer collaboration"
   - Question: "What type of professional partnership interests you?"
   - Sub-choices: Co-founder / business partner, Mentor (seeking), Mentor (offering), Peer collaboration, Advisor / strategic partner, Industry networking
   - Additional info: "Professional matches consider skills, values, ambitions, work style, and complementarity"

   **Option D: Community & Belonging**
   - Icon: Group of people
   - Description: "Find or build communities around shared interests and values"
   - Examples: "Interest-based groups, cause-driven movements, identity-based communities, skill-sharing"
   - Question: "What kind of community are you seeking?"
   - Sub-choices: Hobby/interest, Cause-driven, Identity-based, Location-based, Skill-sharing, Other
   - Additional info: "Community matches group you with people who share passions and create real-world connections"

3. **Select Primary & Secondary Intents**
   - User chooses primary intent (required)
   - User optionally selects secondary intent:
     - "Would you also like to discover [other connection type] connections?"
     - Checkbox: "Yes, also show me [option]"
     - Can select 0-2 secondary intents (total up to 3 active simultaneously)
   - User sees impact: "Your profile will be shown to people seeking [these types] of connections"

4. **Relationship Status & Context (Intent-Specific)**
   - Based on selected intent, user answers clarifying questions:

   **If Dating selected:**
   - "What's your current relationship status?" (Single, Divorced, Widowed, Separated, Complicated, Other)
   - "What's your dating timeline?" (Looking now, Open to meeting, Exploring options, Not sure)
   - "Are you looking for monogamy or open relationships?" (Monogamous, Open/poly, Varies by person, Prefer not to say)
   - "Dealbreakers?" (Checkboxes: Non-negotiables like wanting/not wanting kids, long-distance comfort level, etc.)

   **If Professional selected:**
   - "What stage are you at?" (Actively seeking, Open to opportunities, Exploring, Advising others, Other)
   - "What's your industry/field?" (Free text or category select)
   - "What role are you in?" (Employee, Founder, Investor, Freelancer, Changing careers, Other)

   **If Friendship selected:**
   - "What kind of friend are you?" (Adventure buddy, Emotional support, Fun & social, Intellectual, Mixed)
   - "How often do you want to connect?" (Regularly, Occasional, Spontaneous, Varies)
   - "Do you prefer local or online friendships?" (Local preferred, Online preferred, Flexible, Both)

   **If Community selected:**
   - "What interests/causes matter most to you?" (Multi-select from tags or custom)
   - "Are you looking to join or build?" (Join existing, Start new, Either)
   - "Involvement level?" (Very active, Regular participation, Occasional, Just exploring)

5. **Values & Compatibility Emphasis**
   - Based on intent, ask what matters most in matches:
   - "What's most important for [connection type] compatibility?"
   - Slider scale or ranking (order by importance):
     - Shared values / worldview
     - Shared interests / hobbies
     - Communication style compatibility
     - Life stage / life goals alignment
     - Personal growth potential
     - Fun & chemistry
     - Proximity / logistics
     - Other
   - User ranks top 3-5 by dragging/clicking
   - Visualization: "Your matches will prioritize these factors"

6. **Visibility & Matching Settings (Intent-Specific)**
   - User configures who sees their profile for this intent:
     - "Who can see your profile for [connection type]?"
     - Options: Everyone on platform, Only verified users, Only people I've shown interest in, Hidden (I'll browse only)
   - User sets preference filters:
     - Age range (if dating/romance)
     - Location preferences
     - Deal-breakers (if any)
     - Activity level expectations
     - Other intent-specific filters
   - User controls privacy:
     - "Show my real name?" (First name only, Nickname, Initials, Other)
     - "Show my location?" (Exact, City, Region, Country only, Hidden)
     - "Show my photos in this intent?" (Yes, Only some, Blur faces, No)

7. **Consent for Intent-Specific Matching**
   - User confirms understanding:
     - "I understand my profile will be used to find [connection type] matches using AI analysis"
     - "I understand I can change my intent anytime in settings"
     - "I understand I can match with people on different goals (example: they want dating, I want friendship—we won't match unless both want same thing)"
   - User checks consent boxes

8. **Review & Confirmation**
   - User sees summary:
     - "Primary intent: [Selected]"
     - "Secondary intents: [If selected]"
     - "Relationship/context: [Answers]"
     - "Visibility: [Settings]"
     - "Value priorities: [Ranked]"
   - Call-to-action: "Start discovering connections" or "Adjust settings"
   - Button: "Confirm & Continue"
   - User makes final decision to proceed

### AI Involvement

- **Intent-specific recommendation engine:** AI switches matching algorithm based on selected intent (different algorithms for dating vs. professional vs. friendship)
- **Question personalization:** AI asks follow-up questions specific to selected intent
- **Value analysis:** AI learns which compatibility factors matter most to this user (based on rankings)
- **Profile representation:** AI prepares user profile for matching with the selected intent (emphasizes different aspects for different intents)
- **Match filtering:** AI filters recommendations based on intent compatibility (only shows users who want same type of connection)
- **Notification customization:** AI adjusts notification frequency/style based on intent (daily for dating seekers, weekly for community builders)

### Human Decisions

- User explicitly chooses primary connection intent
- User optionally selects secondary intents
- User answers intent-specific questions about relationship status, timeline, and context
- User ranks what matters most for compatibility
- User configures visibility and matching filters
- User decides on final settings
- User can change intent anytime in settings

### Safety Checks

1. **Intent mismatch prevention:** AI only recommends users who want same type of connection (prevents "surprise dating propositions" for friendship seekers)
2. **Consent logging:** Record explicit consent for intent-based matching
3. **Relationship status verification:** For dating, verify relationship status is accurate (cross-check with other data)
4. **Dealbreaker enforcement:** AI respects dealbreakers (e.g., "no long-distance" users won't be shown long-distance matches)
5. **Privacy enforcement:** Respect visibility settings (don't expose location/photos if user opted out)
6. **Red flag detection:** If user's intent seems predatory (e.g., saying friendship but history of dating advances), flag for review
7. **Minor protection:** If user under 18 (if platform eventually allows), restrict to friendship/community only
8. **Harassment patterns:** If user has history of ignoring rejection, flag in their matching algorithm (matches are more selective)

### Success State

- User explicitly selects at least one connection intent
- User answers all intent-specific clarifying questions
- User ranks value priorities for compatibility
- User configures visibility and matching filters
- User confirms all settings and consent
- Profile is now optimized for matching with selected intent
- AI switches to intent-specific matching algorithm
- User sees confirmation: "Great! Let's find you genuine [connection type] matches."
- User is ready to proceed to Compatibility Discovery (Journey 5, future)
- User is directed to view first AI-generated recommendations

### Failure States

**User stops at any point:**
- Session timeout → Settings saved; user can resume
- Closes app → User prompted to complete on next login
- Skips intent selection → Platform prompts: "Choose at least one connection type to proceed"
- Can't decide → Help text: "You can always change this later. Pick your top priority."
- Selects conflicting intents → AI explains: "Friendship and serious dating are different—you can pursue both, but matches will differ"

**System errors:**
- API fails to update preferences → Graceful error; user can retry
- Recommendations don't load → Cache previous recommendations; show disclaimer "Limited recommendations"

### Edge Cases

1. **Users with non-standard relationship structures**
   - User seeking polyamorous/open matches
   - Option: "I'm in an open/poly relationship" (with partner consent option)
   - Matching algorithm respects these choices
   - Privacy: User controls who knows

2. **Users with changing intents over time**
   - User can change primary/secondary intents anytime
   - Allow up to 3 active intents simultaneously
   - AI re-runs recommendations with new intent filter
   - Option to "pause" an intent (stay in account, don't show new matches for that type)

3. **Users conflicted between intents**
   - Friendly guide: "You can pursue multiple connection types! Most people do."
   - Example: "In the morning, you meet a friendship match. In the evening, you swipe on dating matches."
   - Clarity: "Matches only happen when both people want the same thing"

4. **Users with past trauma or sensitivity**
   - Additional safety controls based on intent
   - Dating: Can require verified profile, ID checks for extra safety
   - Community: Can choose "women only" or other safety-focused communities
   - Option to connect with support resources

5. **Users in high-control relationships**
   - If detect user being monitored/controlled, offer safety resources
   - Can use "hidden mode" where profile doesn't appear publicly
   - Partner can't search their matches

6. **Users with marginalized identities**
   - Special options for LGBTQ+ users:
     - "Sexual orientation" and "Gender identity" with affirming options
     - Can hide these on profile if unsafe
   - Cultural/religious community options
   - Option for "same community only" matching

7. **Users seeking professional opportunities**
   - Clarity: "Professional matching is not networking only—focus is on genuine partnership"
   - Guide: "Be specific about what you're seeking (not just 'want to network')"
   - Options for equity/mentorship arrangements
   - Formalize intentions (e.g., "seek co-founder" vs. "open to mentoring")

8. **International users with regional differences**
   - Clarify intent nuances: Dating norms vary by culture
   - Translate intent descriptions for cultural relevance
   - Allow regional customization (e.g., "Family involvement" preference for cultures where this matters)

9. **Users changing gender identity or sexual orientation**
   - Allow full update without friction
   - Don't force re-verification
   - Discreetly update matching algorithm
   - Option to hide from previous matches/connections

10. **Users with accessibility needs**
    - Provide intent selection in multiple formats (visual cards, text list, voice-guided)
    - All text has clear language explanations
    - Screen reader support for all options
    - Keyboard-only navigation support

---

## Next Journeys (Upcoming)

The following journeys are planned for Phase 2 documentation:

5. Compatibility Discovery
6. AI-Generated Connection Recommendations
7. Reviewing a Recommended Person
8. AI-Assisted Introduction
9. First Conversation
10. Mutual Connection / Acceptance
11. Building an Ongoing Relationship
12. Reporting, Blocking, and Safety Intervention
13. Privacy and Consent Controls
14. Account Deletion and Data Deletion

---

**Document Status:** User Journeys v1.0 (Journeys 1-4 Complete)  
**Last Updated:** 2026-08-20  
**Next Phase:** Journeys 5-14 documentation
