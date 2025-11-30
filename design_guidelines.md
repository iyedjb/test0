# Design Guidelines: Framer Site Iframe with AI Chat Assistant

## Design Approach
**Utility-Focused Overlay Design** - Minimal interference with the iframed content while providing an accessible, modern chat interface.

## Layout System

### Container Structure
- Full viewport container (w-screen h-screen)
- Iframe: Absolute positioning covering entire viewport (inset-0)
- Chat bubble: Fixed positioning in bottom left with consistent spacing from edges
- Spacing units: Tailwind 4, 6, and 8 (p-4, m-6, w-8, etc.)

### Chat Assistant Positioning
- Fixed position: `bottom-6 left-6` (24px from edges)
- Z-index layering: Chat components above iframe (z-50 for bubble, z-40 for expanded chat)

## Component Library

### AI Chat Bubble (Collapsed State)
- Circular button: 14-16 units (56-64px diameter)
- Icon: Message/chat icon from Heroicons (outline style)
- Backdrop blur effect: `backdrop-blur-md backdrop-saturate-150`
- Semi-transparent background for glassy effect
- Shadow: `shadow-2xl` for elevation
- Smooth scale animation on hover: `hover:scale-110 transition-transform duration-200`

### Chat Interface (Expanded State)
- Dimensions: w-96 (384px width), h-[600px] height on desktop
- Mobile responsive: Full width minus spacing (w-[calc(100vw-3rem)])
- Rounded corners: `rounded-2xl` (16px)
- Backdrop blur with semi-transparent background
- Border: Subtle 1px border with low opacity
- Shadow: `shadow-2xl` for strong elevation

### Chat Components Structure
**Header:**
- Height: h-16
- Contains: AI assistant title, minimize/close button
- Border bottom: 1px separator
- Icon: Sparkles or bot icon from Heroicons

**Message Area:**
- Scrollable container: `flex-1 overflow-y-auto`
- Padding: p-4
- Message bubbles: Different alignment for user vs AI
- User messages: Right-aligned, rounded-2xl, max-w-[80%]
- AI messages: Left-aligned, rounded-2xl, max-w-[80%]
- Message spacing: space-y-4

**Input Area:**
- Height: h-20
- Padding: p-4
- Border top: 1px separator
- Input field: Rounded-xl, semi-transparent background
- Send button: Circular, positioned absolute right within input
- Icon: Paper airplane from Heroicons

## Typography

### Font Family
- Primary: `font-sans` (system font stack)
- Google Fonts alternative: Inter via CDN

### Type Scale
- Chat title: text-base font-semibold (16px, 600 weight)
- Messages: text-sm (14px)
- Input placeholder: text-sm (14px)
- Timestamps: text-xs (12px)

## Animations

### Chat Bubble Interactions
- Entrance: Scale and fade-in (`animate-in fade-in slide-in-from-bottom-4 duration-300`)
- Hover: Subtle scale-up (110%)
- Click: Expand to full chat interface with slide-up animation

### Chat Window
- Expand: Slide up with fade-in (`animate-in slide-in-from-bottom-8 fade-in duration-300`)
- Collapse: Slide down with fade-out
- Message appearance: Fade-in with slight slide (`animate-in fade-in slide-in-from-bottom-2 duration-200`)

### Smooth Transitions
- All state changes: `transition-all duration-300 ease-in-out`
- Minimal, purposeful motion - no distracting effects

## Iframe Configuration
- Full coverage: `w-full h-full`
- Border: None
- Allow permissions: `allow="fullscreen"`
- Title attribute for accessibility

## Accessibility
- Chat bubble: `aria-label="Open AI assistant"`
- Expanded chat: `role="dialog"` with proper ARIA labels
- Keyboard navigation: Tab through interactive elements
- Focus states: Visible outline on all interactive elements
- Screen reader announcements for new messages

## Responsive Behavior

### Desktop (lg and above)
- Chat bubble: 64px diameter
- Expanded chat: 384px width, 600px height
- Position: bottom-6 left-6

### Tablet (md)
- Chat bubble: 56px diameter
- Expanded chat: 360px width, 500px height
- Position: bottom-4 left-4

### Mobile (base)
- Chat bubble: 56px diameter
- Expanded chat: Full width minus margins, 70vh height
- Position: bottom-4 left-4

## Visual Treatment Notes
- Glass morphism aesthetic for chat components (blur + semi-transparency)
- Chat should feel modern and non-intrusive
- Subtle shadows for depth without overwhelming the iframe
- Smooth, polished interactions throughout