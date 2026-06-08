# Zaki Chat Pro - Architecture Overview

## System Architecture

```mermaid
graph TB
    subgraph Client["Client Layer"]
        HTML["HTML Structure"]
        CSS["CSS Styling"]
        JS["JavaScript Logic"]
        DOM["DOM Management"]
    end
    
    subgraph UI["User Interface"]
        Header["Header Component<br/>- Title<br/>- Online Status"]
        Chat["Chat Display Area<br/>- Message Container<br/>- Auto-scroll"]
        Input["Input Section<br/>- Text Input<br/>- Send Button"]
    end
    
    subgraph Features["Core Features"]
        SendMsg["Send Message Function"]
        Validation["Input Validation"]
        MsgRender["Message Rendering"]
        Scroll["Auto-scroll to Latest"]
    end
    
    subgraph Styling["Visual Design"]
        Theme["Dark Theme<br/>#0f172a"]
        Gradient["Gradient Header<br/>Green to Blue"]
        Colors["Color Scheme<br/>- Success: #00c853<br/>- Primary: #0091ea"]
    end
    
    Client -->|Controls| UI
    UI -->|Triggers| Features
    Features -->|Updates| DOM
    DOM -->|Renders| Client
    Styling -->|Applies to| UI
```

## Component Breakdown

### 1. **Header Component**
- Green to Blue gradient background
- Application title "Zaki Chat Pro"
- Online status indicator (🟢 Green dot)

### 2. **Chat Display Area**
- Scrollable container (75vh height)
- Messages with rounded corners
- User messages (green, right-aligned)
- Bot messages (dark blue, left-aligned)
- Auto-scroll to latest message

### 3. **Input Section**
- Text input field for messages
- "Dir" (Send) button
- Responsive flex layout

### 4. **Message Flow**

```mermaid
sequenceDiagram
    participant User as User
    participant Input as Input Field
    participant JS as JavaScript Engine
    participant DOM as DOM
    participant UI as Chat Display
    
    User->>Input: Type message
    User->>JS: Click "Dir" button
    JS->>Input: Check if text is empty
    alt Text is not empty
        JS->>DOM: Create new message div
        DOM->>DOM: Set className to "msg me"
        DOM->>UI: Append to chat container
        UI->>UI: Update display
        JS->>Input: Clear input field
        JS->>UI: Scroll to bottom
    else Text is empty
        JS->>JS: Return (do nothing)
    end
```

## Styling Architecture

### Color Palette
```mermaid
graph LR
    A["Dark Background<br/>#0f172a"] 
    B["Secondary Dark<br/>#1e293b"]
    C["Accent Green<br/>#00c853"]
    D["Primary Blue<br/>#0091ea"]
    E["Header Dark<br/>#111827"]
    
    A -->|Base| B
    B -->|Message Container| C
    D -->|Buttons & Accents| E
```

## File Structure

```
zaki/
├── index.html          # Main application file
├── docs/
│   └── architecture.md # This file
└── README.md           # Project documentation
```

## Technology Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | HTML5 |
| **Styling** | CSS3 (Flexbox, Gradients) |
| **Scripting** | JavaScript (Vanilla) |
| **DOM API** | Native Browser APIs |
| **Language Support** | Somali (Af-Soomaali) |

## Key Functions

### `sendMsg()`
```javascript
// Retrieves user input
// Validates against empty strings
// Creates DOM element for message
// Appends to chat container
// Clears input field
// Auto-scrolls to latest message
```

## Features

✅ Real-time message sending  
✅ User input validation  
✅ Auto-scroll functionality  
✅ Responsive design  
✅ Dark theme with gradient header  
✅ Color-coded user vs bot messages  
✅ Online status indicator  
✅ Somali language support  

## Future Enhancements

- [ ] Backend API integration for persistent storage
- [ ] User authentication
- [ ] Typing indicators
- [ ] Message timestamps
- [ ] User avatars
- [ ] Message reactions/emojis
- [ ] Chat history
- [ ] Dark/Light theme toggle
- [ ] Mobile responsiveness improvements
- [ ] Accessibility features (ARIA labels, keyboard navigation)

---

**Created**: 2026-06-08  
**Application**: Zaki Chat Pro  
**Version**: 1.0  
**Status**: ✅ Active Development
