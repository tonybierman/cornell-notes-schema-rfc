# Cornell Notes UX Design Document

**Version:** 1.0
**Author:** Tony Bierman
**Created:** 2026-01-06
**Based on:** Cornell Notes Data Schema RFC v1.0

## Executive Summary

This document defines the user experience design for a digital Cornell Notes application that faithfully implements the five-step Cornell Note-taking methodology: Record, Questions, Recite, Reflect, and Review. The design leverages the Cornell Notes Data Schema to create an intuitive, workflow-driven interface that enhances learning outcomes.

## Table of Contents

1. [Design Philosophy](#design-philosophy)
2. [User Personas](#user-personas)
3. [The Five-Step Workflow](#the-five-step-workflow)
4. [Interface Design](#interface-design)
5. [Feature Specifications](#feature-specifications)
6. [User Flows](#user-flows)
7. [Accessibility](#accessibility)
8. [Technical Integration](#technical-integration)

---

## Design Philosophy

### Core Principles

1. **Workflow-Centric**: The interface guides users through the five-step process naturally
2. **Progressive Disclosure**: Show features when needed, avoid overwhelming users
3. **Minimalist Distraction**: During recording, minimize UI chrome to focus on content
4. **Active Learning**: Encourage engagement through the Questions, Recite, and Reflect phases
5. **Spaced Repetition**: Make weekly reviews easy and rewarding

### Design Goals

- **Reduce friction** in transitioning between the five steps
- **Maintain focus** during lecture recording
- **Encourage completion** of all five steps
- **Build habits** through consistent workflows and reminders
- **Support learning** through evidence-based study techniques

---

## User Personas

### Primary Persona: College Student (Sarah)

- **Age**: 19-22
- **Context**: Attends 4-5 lectures daily, studies for exams
- **Goals**: Retain information, perform well on exams, efficient studying
- **Pain Points**: Too many notes, difficulty finding key information, exam anxiety
- **Device Usage**: Laptop during lectures, mobile for review

### Secondary Persona: Professional Learner (Marcus)

- **Age**: 28-45
- **Context**: Attends conferences, training sessions, webinars
- **Goals**: Apply knowledge to work, reference materials later
- **Pain Points**: Interruptions, context switching, scattered notes
- **Device Usage**: Tablet/laptop during sessions, mobile during commute

### Tertiary Persona: High School Student (Emma)

- **Age**: 15-18
- **Context**: Multiple classes daily, standardized test preparation
- **Goals**: Understand concepts, prepare for tests, maintain grades
- **Pain Points**: Information overload, study technique uncertainty
- **Device Usage**: Mixed (laptop/tablet/mobile)

---

## The Five-Step Workflow

### Step 1: Record (During Lecture)

**Objective**: Capture lecture content using telegraphic sentences in the notes column.

#### UX Requirements

- **Full-screen or distraction-free mode**
- **Fast input** with minimal UI interference
- **Automatic timestamping** of notes
- **Quick formatting** (bullets, numbering, code blocks)
- **Lightweight metadata capture** (subject, topic auto-filled)

#### Interface Elements

- Large notes column (right side, ~70% width)
- Minimal cue column visible (left side, ~30% width, greyed out/locked)
- Summary section hidden during recording
- Toolbar: minimal formatting only (bold, italic, list, code)
- Status bar: note count, timestamp, word count
- Mode indicator: "Recording Mode"

#### Key Interactions

- **Tab key**: Quick bullet point
- **Enter**: New note entry
- **Cmd/Ctrl + K**: Insert link
- **Cmd/Ctrl + Shift + C**: Insert code block
- **Auto-save**: Every 30 seconds
- **Background sync**: Cloud backup

### Step 2: Questions (After Lecture)

**Objective**: Formulate questions and cue words in the cue column to clarify and organize notes.

#### UX Requirements

- **Easy transition** from Record to Questions mode
- **Side-by-side view** of cues and notes
- **Visual linking** between cues and related notes
- **Question templates** and prompts
- **Smart suggestions** based on note content

#### Interface Elements

- Split view: Cue column (30%) | Notes column (70%)
- Notes column: Read-only or lightly editable
- Cue column: Active editing area
- Mode indicator: "Questions Mode"
- Sidebar: Question type selector (question, keyword, concept)
- AI assistant panel (optional): Suggests questions based on notes

#### Key Interactions

- **Click note → Generate cue**: Auto-creates cue linked to clicked note
- **Drag to link**: Drag cue to note to create relationship
- **Question type selector**: Dropdown for question/keyword/concept
- **Template shortcuts**:
  - `?` → Question format
  - `#` → Keyword format
  - `!` → Key concept format
- **Auto-link suggestions**: Highlight notes when creating cues
- **Smart completion**: Suggest cues based on note content

#### Question Prompts

- "What is the main idea here?"
- "How does this relate to previous concepts?"
- "What are the key terms?"
- "Why is this important?"

### Step 3: Recite (Study Phase 1)

**Objective**: Test recall by covering notes and answering questions aloud.

#### UX Requirements

- **Hide/show toggle** for notes column
- **Progressive reveal** mode
- **Voice recording** option (optional)
- **Self-assessment** mechanism
- **Spaced repetition scheduling**

#### Interface Elements

- Study mode UI:
  - Cue column: Visible, full width initially
  - Notes column: Hidden behind curtain/blur
  - Reveal button: "Show Answer"
  - Self-assessment buttons: "Got It" / "Review Again" / "Difficult"
- Progress indicator: X of Y cues completed
- Timer: Track study duration
- Mode indicator: "Recite Mode"

#### Key Interactions

1. **Start Recite**: User clicks "Begin Recite Mode"
2. **View cue**: First cue displayed prominently
3. **Attempt recall**: User tries to remember answer
4. **Reveal answer**: Click to show linked notes
5. **Self-assess**: Rate confidence (Got It/Review/Difficult)
6. **Next cue**: Automatically advances
7. **Track results**: System records performance for spaced repetition

#### Voice Recording (Optional Enhancement)

- Record button: Capture verbal answer
- Playback: Compare with written notes
- Speech-to-text: Auto-transcribe for review

### Step 4: Reflect (Study Phase 2)

**Objective**: Deepen understanding through reflective questions about significance, principles, and applications.

#### UX Requirements

- **Reflection prompts** tailored to content
- **Writing space** for reflective notes
- **Connection mapping** to prior knowledge
- **Synthesis tools** for cross-note insights

#### Interface Elements

- Reflection panel: Opens after Recite or independently
- Prompt cards: Rotating reflective questions
- Free-form text area: Journal-style reflection space
- Connection mapper: Visual graph of related concepts
- Summary section: Becomes editable
- Mode indicator: "Reflect Mode"

#### Reflection Prompts

The system displays these prompts one at a time:

1. "What's the significance of these concepts?"
2. "What principles are they based on?"
3. "How can I apply this knowledge?"
4. "How does this fit with what I already know?"
5. "What questions remain? What's beyond this?"
6. "How would I explain this to someone else?"

#### Key Interactions

- **Prompt rotation**: Swipe/arrow to cycle through prompts
- **Write reflection**: Type response in dedicated area
- **Link notes**: Tag which cues/notes the reflection references
- **Save to summary**: Option to incorporate reflection into summary
- **Create connections**: Link to other Cornell Note documents
- **Concept map**: Visual representation of connections

### Step 5: Review (Weekly Habit)

**Objective**: Spend 10+ minutes weekly reviewing all previous notes for retention.

#### UX Requirements

- **Review dashboard** showing all notes
- **Smart scheduling** for spaced repetition
- **Quick scan** interface
- **Progress tracking** and streaks
- **Reminders and notifications**

#### Interface Elements

- Review Dashboard:
  - Calendar view: Notes by date
  - Due for review: Notes needing attention
  - Review streak: Days/weeks of consistent review
  - Quick stats: Total notes, review rate, retention estimate
- List view: All Cornell Notes sortable by:
  - Due date (spaced repetition)
  - Subject
  - Last reviewed
  - Creation date
- Batch review mode: Quick flip-through of multiple notes
- Mode indicator: "Review Mode"

#### Key Interactions

- **Start review session**: Click "Begin Weekly Review"
- **Queue generation**: System selects notes based on:
  - Spaced repetition algorithm
  - Last review date
  - User-marked difficulty
  - Subject/topic grouping
- **Quick review flow**:
  1. Show note title and summary
  2. Quick scan of cues
  3. Optionally expand to full recite mode
  4. Mark as reviewed
  5. Next note
- **Review timer**: 10-minute minimum countdown
- **Completion celebration**: Visual feedback on completing review

#### Spaced Repetition Algorithm

- First review: 1 day after creation
- Second review: 3 days after first review
- Third review: 7 days after second review
- Fourth review: 14 days after third review
- Subsequent: 30 days, then monthly
- Adjust based on self-assessment (difficult = shorter interval)

---

## Interface Design

### Layout Structure

#### Three-Column Layout (Desktop)

```
┌─────────────────────────────────────────────────────────┐
│  Header: [Title] [Subject] [Mode] [User Menu]          │
├──────────┬─────────────────────────────────┬────────────┤
│          │                                 │            │
│   Cue    │         Notes Column            │  Sidebar   │
│  Column  │                                 │  (Context) │
│  (30%)   │           (50%)                 │   (20%)    │
│          │                                 │            │
│          │                                 │            │
└──────────┴─────────────────────────────────┴────────────┘
│                  Summary Section                        │
│                   (Collapsible)                         │
└─────────────────────────────────────────────────────────┘
```

#### Mobile Layout (Stacked)

```
┌─────────────────────┐
│  Header             │
├─────────────────────┤
│  Tab: [Cues|Notes]  │
├─────────────────────┤
│                     │
│   Active Content    │
│   (Full Width)      │
│                     │
└─────────────────────┘
│     Summary         │
└─────────────────────┘
```

### Mode-Specific Views

#### Recording Mode
- Notes column: Full focus
- Cue column: Minimized or hidden
- Summary: Hidden
- Toolbar: Minimal
- Distractions: None

#### Questions Mode
- Cue column: Active editing
- Notes column: Reference (read-only)
- Summary: Hidden
- Sidebar: Question templates and AI suggestions

#### Recite Mode
- Cue column: Full width, prominent
- Notes column: Hidden/blurred
- Reveal button: Centered
- Self-assessment: Bottom of screen

#### Reflect Mode
- Notes column: Read-only reference
- Reflection panel: Center stage
- Summary: Editable
- Prompt cards: Rotating display

#### Review Mode
- Dashboard: List/calendar view
- Quick preview: Title + summary cards
- Batch actions: Mark reviewed, reschedule

### Visual Design

#### Color System

**Mode Colors** (subtle background tints):
- Record: Blue (#E3F2FD)
- Questions: Green (#E8F5E9)
- Recite: Orange (#FFF3E0)
- Reflect: Purple (#F3E5F5)
- Review: Teal (#E0F2F1)

**Status Colors**:
- Success/Got It: Green (#4CAF50)
- Review Again: Yellow (#FFC107)
- Difficult: Red (#F44336)
- Neutral: Grey (#9E9E9E)

#### Typography

- **Headings**: System font, bold, 24px (title), 18px (section)
- **Body text**: System font, regular, 16px (notes), 14px (cues)
- **Code**: Monospace, 14px
- **Line height**: 1.6 for readability

#### Spacing

- Column gaps: 24px
- Section padding: 16px
- Card spacing: 12px
- Compact mode: 8px padding

### Component Library

#### Note Card
- Rounded corners (8px)
- Subtle shadow
- Hover state: Lift effect
- Active state: Border highlight

#### Cue Item
- Pill shape for keywords
- Question icon for questions
- Numbered list for sequences
- Link indicator for connected notes

#### Summary Box
- Distinct background color
- Larger font size
- Collapsible with smooth animation
- Edit toggle button

---

## Feature Specifications

### Core Features

#### 1. Mode Switching

**Requirement**: Seamless transition between the five modes.

**Implementation**:
- Mode selector: Dropdown or tab bar
- Keyboard shortcuts: Cmd/Ctrl + 1-5
- Auto-suggest next mode: "Ready to add questions?"
- Save state: Preserve work when switching modes

#### 2. Auto-Linking

**Requirement**: Connect cues to related notes automatically and manually.

**Implementation**:
- AI suggestion: Analyze note content to suggest cue placement
- Manual linking: Drag-and-drop or click to link
- Visual indicators: Line/highlight showing connections
- Bulk linking: Link one cue to multiple notes
- Schema mapping: Store in `cueLinks` array

#### 3. Spaced Repetition

**Requirement**: Schedule reviews based on learning science.

**Implementation**:
- Algorithm: SM-2 or custom variant
- Difficulty adjustment: User feedback influences schedule
- Review queue: Daily/weekly batches
- Analytics: Track retention over time
- Notifications: Remind users of due reviews

#### 4. Search and Filter

**Requirement**: Find notes quickly across all documents.

**Implementation**:
- Full-text search: All fields (title, subject, notes, cues, summary)
- Filters: Subject, topic, tags, date range
- Saved searches: Quick access to common queries
- Search within: Limit scope to current note or all notes
- Results preview: Highlight matching text

#### 5. Export and Import

**Requirement**: Share and backup notes in multiple formats.

**Implementation**:
- Export formats: PDF, Markdown, HTML, JSON
- Import: Cornell JSON schema, plain text parsing
- Batch export: Multiple notes at once
- Cloud sync: Automatic backup
- Print: Formatted for traditional Cornell layout

### Enhanced Features

#### 6. AI Assistant

**Capability**: Help users create better questions and reflections.

**Features**:
- Question generation: Suggest cues based on notes
- Summary creation: Draft summary from notes
- Reflection prompts: Personalized based on content
- Knowledge gaps: Identify missing connections
- Study tips: Recommend study strategies

#### 7. Collaboration

**Capability**: Share and collaborate on notes.

**Features**:
- Shared notes: View/edit permissions
- Comments: Discuss specific cues or notes
- Merge notes: Combine multiple students' notes
- Public sharing: Export view-only link
- Version history: Track changes over time

#### 8. Analytics

**Capability**: Understand study patterns and effectiveness.

**Features**:
- Study time: Track minutes spent in each mode
- Retention metrics: Success rate in Recite mode
- Coverage: Percentage of notes reviewed weekly
- Streaks: Consecutive days/weeks of review
- Subject breakdown: Study time per subject
- Insights: "You review math notes 30% more than history"

#### 9. Templates

**Capability**: Quick-start notes for different scenarios.

**Features**:
- Subject templates: Pre-filled structures for common topics
- Question templates: Standard question formats
- Custom templates: User-created patterns
- Template library: Community-shared templates

#### 10. Voice and Audio

**Capability**: Hands-free and auditory learning.

**Features**:
- Voice input: Dictate notes during recording
- Text-to-speech: Listen to notes during review
- Audio notes: Record lecture audio linked to text notes
- Voice recite: Record answers during Recite mode
- Podcast export: Convert notes to audio format

---

## User Flows

### Flow 1: Complete First Note

**Scenario**: Sarah attends her first lecture and creates a Cornell Note.

1. **Launch app** → Welcome screen
2. **Click "New Note"** → Recording mode opens
3. **Enter title**: "Introduction to Psychology - Lecture 1"
4. **Type notes** during lecture:
   - "Behavior shaped by nature and nurture"
   - "Cognitive psychology studies mental processes"
   - "Behaviorism focuses on observable actions"
5. **Lecture ends** → Click "Finish Recording"
6. **Prompt appears**: "Great! Now let's add questions to your notes."
7. **Switch to Questions mode** → Cue column activates
8. **Add cues**:
   - "Nature vs nurture?" → Links to first note
   - "What is cognitive psych?" → Links to second note
   - "Define behaviorism" → Links to third note
9. **Click "Done with Questions"** → Prompt: "Want to test your recall?"
10. **Enter Recite mode** → First cue appears
11. **Read cue**, try to remember → Click "Show Answer"
12. **Review note** → Click "Got It"
13. **Next cue** → Repeat for all cues
14. **Recite complete** → Prompt: "Take a moment to reflect"
15. **Enter Reflect mode** → Prompt: "How does this fit with what you know?"
16. **Type reflection**: "Connects to biology class discussions on genetics"
17. **Write summary**: "Psychology studies behavior through multiple lenses..."
18. **Save note** → Added to review schedule
19. **Confirmation**: "Your note is ready! We'll remind you to review in 1 day."

**Total time**: 45 minutes (30 min lecture + 15 min questions/recite/reflect)

### Flow 2: Weekly Review Session

**Scenario**: Marcus completes his weekly review on Sunday morning.

1. **Open app** → Dashboard shows "8 notes due for review"
2. **Click "Start Weekly Review"** → Review mode opens
3. **First note appears**: Title and summary preview
4. **Quick scan**: Read summary, glance at cues
5. **Click "Full Recite"** → Enter Recite mode
6. **Test knowledge**: Go through cues
7. **Self-assess**: Mark as "Got It"
8. **Return to review queue** → Next note appears
9. **Repeat** for all 8 notes
10. **Timer hits 10 minutes** → "Great job! Minimum review time reached"
11. **Complete all notes** → Celebration screen
12. **Stats display**: "100% review completion, 7-day streak!"
13. **Next review**: "Come back in 3 days for 4 more notes"

**Total time**: 12 minutes

### Flow 3: Mobile Quick Review (During Commute)

**Scenario**: Emma reviews notes on the bus using her phone.

1. **Open mobile app** → Review dashboard
2. **Tap "Quick Review"** → First note loads
3. **Swipe through cues** → Read each one
4. **Tap difficult cue** → Notes reveal, marked for later
5. **Swipe to next note** → Continue reviewing
6. **5 minutes pass** → Pause and save progress
7. **Resume later** → Picks up where left off

**Total time**: 5 minutes (partial session)

---

## Accessibility

### WCAG 2.1 AA Compliance

#### Visual

- **Contrast ratios**: Minimum 4.5:1 for text
- **Font scaling**: Support up to 200% zoom
- **Color independence**: Don't rely solely on color for meaning
- **Focus indicators**: Clear keyboard focus outlines
- **Dark mode**: Full support with proper contrast

#### Auditory

- **Screen reader**: Full ARIA labels and semantic HTML
- **Alt text**: All images and icons described
- **Keyboard navigation**: All features accessible via keyboard
- **Audio descriptions**: For video content

#### Motor

- **Large touch targets**: Minimum 44x44px
- **Keyboard shortcuts**: Configurable and documented
- **Voice control**: Compatible with OS voice commands
- **No time limits**: Allow users to work at their own pace

#### Cognitive

- **Simple language**: Clear, concise instructions
- **Consistent layout**: Predictable UI patterns
- **Progressive disclosure**: Don't overwhelm with options
- **Undo/redo**: Easy error recovery
- **Auto-save**: Prevent data loss

### Internationalization

- **RTL support**: Right-to-left languages (Arabic, Hebrew)
- **Date/time formats**: Locale-specific
- **Translation ready**: All strings externalized
- **Unicode support**: Emoji, special characters

---

## Technical Integration

### Schema Mapping

#### Recording Mode → Schema

```json
{
  "metadata": {
    "title": "[User input]",
    "subject": "[User input or auto-detected]",
    "created": "[Auto: ISO timestamp]",
    "modified": "[Auto: updates on save]"
  },
  "sections": [{
    "notes": [
      {
        "content": "[User types here]",
        "type": "text|list|code",
        "position": "[Auto-incremented]",
        "created": "[Auto]",
        "modified": "[Auto]"
      }
    ]
  }]
}
```

#### Questions Mode → Schema

```json
{
  "sections": [{
    "cues": [
      {
        "content": "[User creates questions]",
        "type": "question|keyword|text",
        "position": "[Auto]"
      }
    ],
    "notes": [
      {
        "cueLinks": ["[UUID of linked cue]"]
      }
    ]
  }]
}
```

#### Reflect Mode → Schema

```json
{
  "summary": {
    "content": "[User writes reflection/summary]",
    "created": "[Auto]",
    "modified": "[Auto]"
  }
}
```

### Additional Schema Extensions

To support the five-step workflow, we'll need optional metadata extensions:

```json
{
  "studyMetadata": {
    "reciteHistory": [
      {
        "timestamp": "ISO 8601",
        "cueId": "UUID",
        "assessment": "got_it|review|difficult"
      }
    ],
    "reviewSchedule": {
      "lastReviewed": "ISO 8601",
      "nextReview": "ISO 8601",
      "interval": "integer (days)"
    },
    "reflections": [
      {
        "timestamp": "ISO 8601",
        "prompt": "string",
        "response": "string"
      }
    ],
    "modeCompletions": {
      "record": "ISO 8601",
      "questions": "ISO 8601",
      "recite": "ISO 8601",
      "reflect": "ISO 8601",
      "review": ["ISO 8601"]
    }
  }
}
```

### State Management

#### Mode State

```javascript
const modes = {
  RECORD: 'record',
  QUESTIONS: 'questions',
  RECITE: 'recite',
  REFLECT: 'reflect',
  REVIEW: 'review'
};

const modeState = {
  current: 'record',
  completed: [],
  canTransition: (fromMode, toMode) => {
    // Logic to determine valid transitions
  }
};
```

#### UI State

```javascript
const uiState = {
  notesVisible: true,
  cuesVisible: true,
  summaryVisible: false,
  sidebarPanel: null, // 'templates' | 'ai' | 'analytics' | null
  currentCueIndex: 0,
  reciteProgress: { current: 0, total: 10 }
};
```

### Persistence Strategy

- **Auto-save**: Every 30 seconds during active editing
- **Cloud sync**: Background sync to server
- **Local-first**: IndexedDB for offline access
- **Conflict resolution**: Last-write-wins with merge option
- **Version history**: Store previous versions for 30 days

---

## Implementation Roadmap

### Phase 1: Core Workflow (MVP)

**Duration**: 8-10 weeks

- Recording mode with basic formatting
- Questions mode with manual linking
- Recite mode with hide/reveal
- Basic summary editing
- Simple review list
- Export to PDF and JSON

### Phase 2: Enhanced Study Features

**Duration**: 6-8 weeks

- Spaced repetition algorithm
- Review dashboard with scheduling
- Analytics and progress tracking
- Mobile responsive design
- Cloud sync and backup

### Phase 3: Advanced Features

**Duration**: 8-10 weeks

- AI assistant for question generation
- Voice input and text-to-speech
- Collaboration and sharing
- Template library
- Advanced search and filters

### Phase 4: Polish and Optimization

**Duration**: 4-6 weeks

- Performance optimization
- Accessibility audit and fixes
- User testing and iteration
- Onboarding flow
- Documentation and help system

---

## Success Metrics

### Engagement Metrics

- **Completion rate**: % of users who complete all 5 steps
- **Recite frequency**: Average recite sessions per note
- **Review adherence**: % of scheduled reviews completed
- **Session duration**: Time spent in each mode
- **Retention**: 7-day, 30-day user retention

### Learning Metrics

- **Recite success**: % of cues marked "Got It"
- **Review consistency**: Weekly review streak
- **Note coverage**: % of notes reviewed regularly
- **Reflection depth**: Average reflection word count

### Feature Adoption

- **AI usage**: % of users using AI suggestions
- **Voice features**: % of users using voice input/TTS
- **Export usage**: Number of exports per user
- **Collaboration**: % of users sharing notes

### User Satisfaction

- **NPS score**: Net Promoter Score
- **Feature ratings**: Individual feature satisfaction
- **Support tickets**: Volume and type
- **User feedback**: Qualitative insights

---

## Appendix A: Keyboard Shortcuts

### Global Shortcuts

| Shortcut | Action |
|----------|--------|
| Cmd/Ctrl + N | New note |
| Cmd/Ctrl + S | Save note |
| Cmd/Ctrl + F | Search |
| Cmd/Ctrl + 1 | Record mode |
| Cmd/Ctrl + 2 | Questions mode |
| Cmd/Ctrl + 3 | Recite mode |
| Cmd/Ctrl + 4 | Reflect mode |
| Cmd/Ctrl + 5 | Review mode |

### Recording Mode

| Shortcut | Action |
|----------|--------|
| Tab | Insert bullet point |
| Cmd/Ctrl + B | Bold |
| Cmd/Ctrl + I | Italic |
| Cmd/Ctrl + K | Insert link |
| Cmd/Ctrl + Shift + C | Code block |

### Recite Mode

| Shortcut | Action |
|----------|--------|
| Space | Reveal answer |
| 1 | Got it |
| 2 | Review again |
| 3 | Difficult |
| → | Next cue |
| ← | Previous cue |

---

## Appendix B: Mobile Adaptations

### Touch Gestures

- **Swipe left**: Next note/cue
- **Swipe right**: Previous note/cue
- **Swipe up**: Show summary
- **Swipe down**: Hide summary
- **Long press**: Edit mode
- **Double tap**: Toggle reveal (Recite mode)
- **Pinch**: Zoom text

### Mobile-Specific Features

- **Quick capture**: Widget for fast note creation
- **Offline mode**: Full functionality without network
- **Audio recording**: Link to note sections
- **Camera**: Capture whiteboard/slides
- **Notification reminders**: Review alerts

---

## Appendix C: Wireframes

### Recording Mode

```
┌─────────────────────────────────────────┐
│ Intro to Psychology - Lecture 1    [×] │
├─────────────────────────────────────────┤
│ 📝 Recording Mode          [Stop & Save]│
├─────────────────────────────────────────┤
│                                         │
│  Notes                                  │
│  ┌───────────────────────────────────┐ │
│  │ • Behavior shaped by nature and   │ │
│  │   nurture                         │ │
│  │                                   │ │
│  │ • Cognitive psychology studies    │ │
│  │   mental processes                │ │
│  │                                   │ │
│  │ • Behaviorism focuses on          │ │
│  │   observable actions              │ │
│  │                                   │ │
│  │ [Cursor here...]                  │ │
│  └───────────────────────────────────┘ │
│                                         │
│  [B] [I] [•] [1.] [</>] [🔗]          │
└─────────────────────────────────────────┘
  3 notes • 10:45 AM • Auto-saved
```

### Questions Mode

```
┌──────────────────────────────────────────────────┐
│ Intro to Psychology - Lecture 1             [×] │
├──────────────────────────────────────────────────┤
│ ❓ Questions Mode    [Done] [🤖 AI Suggestions] │
├────────────┬─────────────────────────────────────┤
│ Cues       │ Notes                               │
├────────────┼─────────────────────────────────────┤
│ ? Nature   │ • Behavior shaped by nature and ◄───┤
│   vs       │   nurture                           │
│   nurture? │                                     │
│            │                                     │
│ ? What is  │ • Cognitive psychology studies  ◄───┤
│   cognitive│   mental processes                  │
│   psych?   │                                     │
│            │                                     │
│ # Behavior-│ • Behaviorism focuses on        ◄───┤
│   ism      │   observable actions                │
│            │                                     │
│ [Add cue]  │                                     │
└────────────┴─────────────────────────────────────┘
```

### Recite Mode

```
┌─────────────────────────────────────────┐
│ 🧠 Recite Mode                      [×] │
├─────────────────────────────────────────┤
│                                         │
│         Cue 1 of 3                      │
│                                         │
│    ┌─────────────────────────────┐     │
│    │                             │     │
│    │  ? Nature vs nurture?       │     │
│    │                             │     │
│    └─────────────────────────────┘     │
│                                         │
│         [Show Answer]                   │
│                                         │
│                                         │
│  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━    │
│  Progress: ██████░░░░░░░░░░░░ 33%      │
└─────────────────────────────────────────┘

[After clicking Show Answer]

┌─────────────────────────────────────────┐
│ 🧠 Recite Mode                      [×] │
├─────────────────────────────────────────┤
│                                         │
│    ? Nature vs nurture?                 │
│                                         │
│    ┌─────────────────────────────────┐ │
│    │ Answer:                         │ │
│    │                                 │ │
│    │ Behavior shaped by nature and   │ │
│    │ nurture                         │ │
│    └─────────────────────────────────┘ │
│                                         │
│  How well did you remember?             │
│                                         │
│  [✓ Got It]  [↻ Review]  [! Difficult] │
│                                         │
│  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━    │
│  Progress: ██████░░░░░░░░░░░░ 33%      │
└─────────────────────────────────────────┘
```

### Review Dashboard

```
┌─────────────────────────────────────────┐
│ 📚 Review Dashboard                 [×] │
├─────────────────────────────────────────┤
│                                         │
│  This Week                              │
│  ┌───────────────────────────────────┐ │
│  │ 🔥 7-day streak                   │ │
│  │ ✓ 12 of 15 notes reviewed         │ │
│  │ ⏱ 45 minutes study time           │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Due for Review (3)    [Start Review]  │
│  ┌───────────────────────────────────┐ │
│  │ Intro to Psychology - Lecture 1   │ │
│  │ Psychology • 2 days ago           │ │
│  ├───────────────────────────────────┤ │
│  │ Chemical Reactions                │ │
│  │ Chemistry • 1 week ago            │ │
│  ├───────────────────────────────────┤ │
│  │ World War II Timeline             │ │
│  │ History • 3 days ago              │ │
│  └───────────────────────────────────┘ │
│                                         │
│  Recent Notes (5)                       │
│  [Grid view of recent note cards...]   │
└─────────────────────────────────────────┘
```

---

## Document Changelog

- **v1.0** (2026-01-06): Initial UX design specification
