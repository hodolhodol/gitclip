# Clipboard Sync Tool Implementation Plan (Unified Web App)

## Goal Description
Create a responsive web application that acts as a clipboard bridge between devices (Company PC and Smartphone).
**Rationale**: A web-based approach is zero-install, works on any device with a browser, and avoids security restrictions associated with installing extensions or running scripts.

## User Review Required
> [!IMPORTANT]
> **Hosting**: You can simply open the `index.html` file locally in your browser, or host it on **GitHub Pages** for easy access from both devices.
> **Security**: The GitHub Personal Access Token (PAT) will be stored in the browser's **LocalStorage**. It is never sent to any server other than GitHub's official API.

## Proposed Changes

### Architecture
*   **Backend**: GitHub Gist (Secret).
*   **Frontend**: Single Page Application (HTML/CSS/JS).
    *   **Responsive**: Layout adapts to Desktop (PC) and Mobile screens.
    *   **Logic**: Uses `fetch` API to read/write to Gist.

### Web Application V2 (Single File)
Located in `d:/dev/manual/gitclip/index.html` (Unified single file).

#### [MODIFY] [index.html](file:///d:/dev/manual/gitclip/index.html)
*   **Design**:
    *   **Header**: Title + Gear Icon (Settings Toggle).
    *   **Settings**: Overlay/Slide-down panel. Added **[Secret Password]** field for encryption.
    *   **Controls**: Row of buttons. Load/Save take priority. Copy/Clear use SVGs.
*   **Design**:
    *   **Header**: Title + Lock Icon + Gear Icon.
    *   **Settings**: Add **[Device Name]** field to identify who is saving.
    *   **History**: Now displays **Global History** from the Cloud.
        *   Items show: `[Device Name]`, `[Read Count]`, `Timestamp`, `Content Preview`.
*   **Logic**:
    *   **Data Structure**: Switch from `clipboard.txt` to `gitclip_data.json`.
        *   Format: `Array<{ content, device, timestamp, reads, iv, salt }>`
    *   **Sync**:
        *   **Save**: Fetch JSON -> Prepend new item -> Save JSON.
        *   **Load**: Fetch JSON -> Increment `reads` of top item -> Save JSON (bg) -> Display content.
    *   **Encryption**: Keep treating `content` as the encrypted payload. Metadata is plain text.
    *   **Migration**: If `clipboard.txt` exists but json doesn't, migrate it once.
    *   **Icons**: Use inline SVGs for zero dependencies.
    *   **Status**: Fixed footer.

## Verification Plan
### Manual Verification
1.  **UI**: Verify Settings toggles correctly. Buttons are aligned.
2.  **History**:
    *   Perform Load -> Check if "⬇️ [Time] Content..." appears in history.
    *   Perform Save -> Check if "⬆️ [Time] Content..." appears in history.
    *   Click History Item -> Verify text content is correct and Copy works.
3.  **Mobile**: Deploy to GitHub Pages and verify touch targets and layout.
