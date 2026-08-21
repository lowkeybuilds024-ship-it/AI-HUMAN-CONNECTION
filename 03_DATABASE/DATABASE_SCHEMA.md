# DATABASE SCHEMA

## AI-HUMAN-CONNECTION MVP

## 1. Database Goals

The database must be:
- Secure
- Privacy-first
- Scalable
- Consistent
- Auditable
- Designed for the MVP

## 2. Core Entities

The MVP database contains:

1. Users
2. Profiles
3. Preferences
4. Connection Intents
5. Compatibility Scores
6. Matches
7. Conversations
8. Messages
9. Reports
10. Blocks
11. Verification Records
12. Consent Records
13. Notifications
14. Moderation Actions
15. Audit Logs

## 3. Users

Stores account-level information.

Fields:
- id
- email
- password_hash
- account_status
- email_verified
- created_at
- updated_at
- last_login_at

Rules:
- Never store plain-text passwords.
- Use unique user IDs.
- Account status must support active, suspended and deleted states.

## 4. Profiles

Stores user-provided profile information.

Fields:
- id
- user_id
- display_name
- date_of_birth
- bio
- location
- profile_photo
- interests
- values
- lifestyle_information
- visibility_status
- created_at
- updated_at

Privacy:
- Only approved profile information should be exposed to other users.

## 5. Preferences

Stores matching preferences.

Fields:
- id
- user_id
- preferred_age_range
- preferred_location
- relationship_goal
- interests
- values
- dealbreakers
- matching_enabled
- created_at
- updated_at

## 6. Connection Intents

Stores the user's selected connection purpose.

MVP:
- Dating

Future:
- Friendship
- Professional
- Community

Fields:
- id
- user_id
- intent_type
- intent_details
- active
- created_at
- updated_at

## 7. Compatibility Scores

Stores AI-generated compatibility information.

Fields:
- id
- user_id
- candidate_user_id
- compatibility_score
- explanation
- model_version
- generated_at

Important:
- AI scores are recommendations, not decisions.
- Store model version for explainability and auditing.

## 8. Matches

Stores connection decisions.

Fields:
- id
- user_id
- matched_user_id
- status
- created_at
- updated_at

Possible statuses:
- suggested
- connected
- rejected
- blocked
- expired

## 9. Conversations

Stores conversation-level information.

Fields:
- id
- match_id
- created_at
- updated_at
- status

## 10. Messages

Stores messages between matched users.

Fields:
- id
- conversation_id
- sender_id
- message_text
- moderation_status
- created_at

Security:
- Messages must be protected from unauthorized access.
- Moderation processing must respect privacy requirements.

## 11. Reports

Stores safety reports.

Fields:
- id
- reporter_id
- reported_user_id
- category
- description
- status
- created_at
- resolved_at

## 12. Blocks

Stores blocking relationships.

Fields:
- id
- blocker_id
- blocked_user_id
- created_at

Rule:
Blocked users must not appear in matching or messaging.

## 13. Verification Records

Fields:
- id
- user_id
- verification_type
- status
- verified_at
- created_at

Sensitive verification data must be minimized and protected.

## 14. Consent Records

Stores important user consent.

Fields:
- id
- user_id
- consent_type
- consent_version
- granted
- granted_at
- revoked_at

Examples:
- Terms acceptance
- Privacy consent
- AI matching consent
- Data processing consent

## 15. Notifications

Fields:
- id
- user_id
- notification_type
- title
- message
- read_status
- created_at

## 16. Moderation Actions

Fields:
- id
- moderator_id
- target_user_id
- action_type
- reason
- created_at

## 17. Audit Logs

Stores important security and administrative events.

Fields:
- id
- actor_id
- action
- target_type
- target_id
- metadata
- created_at

Audit logs must not expose unnecessary sensitive information.

## 18. Relationships

```text
Users
  │
  ├── Profiles
  ├── Preferences
  ├── Connection Intents
  ├── Verification Records
  ├── Consent Records
  ├── Notifications
  ├── Reports
  └── Blocks
        │
        ↓
      Matches
        │
        ↓
   Conversations
        │
        ↓
     Messages

Users ──→ Compatibility Scores
Users ──→ Moderation Actions
Users ──→ Audit Logs
