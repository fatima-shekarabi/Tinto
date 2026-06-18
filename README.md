# Tinto

Tinto is an iOS and iPadOS app that turns a museum visit into a hands-on creative activity for kids aged 6 to 11. Children scan a painting, learn its colors, unlock them through a mixing mini-game, and then recreate the artwork in their own style, by drawing on screen or "painting in the air" with AR.

## Features

- **Scan a painting**, the camera extracts the artwork's dominant colors and detects its style
- **Mix to unlock**, a color-mixing mini-game (red, yellow, blue, white, black) where kids match a target color to add it to their palette, with stars, streaks, and a bit of celebration when they nail it
- **Two ways to paint**
  - Touch canvas, using a finger or Apple Pencil (PencilKit)
  - AR canvas, where the child's hand becomes the brush
- **Personal gallery**, finished paintings are saved to a flippable wall alongside the original artwork photo
- **Badges**, small milestones (first painting, color master, gallery star, etc.) tracked locally
- **Sharing**, export a single painting or the whole gallery through the standard iOS share sheet
- **English and Italian**, fully localized, switchable from inside the app
- **Light/dark appearance, custom avatar, name and age**

## Tech stack

- Swift and SwiftUI, targeting iOS 16.0+
- PencilKit for drawing
- AVFoundation for camera capture
- On-device color extraction and art-style detection (with an optional FoundationModels path on iOS 26+, falling back to a heuristic on earlier versions)
- AudioToolbox for lightweight sound effects, no audio assets, no third-party libraries
- FileManager-based local storage for paintings, photos, and metadata, nothing leaves the device

No third-party dependencies are used anywhere in the project.

## Project structure

```
Tinto/
├── TintoApp.swift                   # App entry point
├── RootView.swift                   # Root navigation / onboarding
├── OnboardingView.swift             # First-launch onboarding flow
├── CameraScreen.swift               # Artwork scanning
├── ColorExtractor.swift             # Dominant color extraction
├── ArtStyleDetector.swift           # Style detection (heuristic + FoundationModels)
├── PaintingStyleDetector.swift      # Supporting style classification logic
├── ColorGameView.swift              # Color-mixing mini-game
├── ColorPreviewScreen.swift         # Color palette preview
├── CanvasSelectionView.swift        # Choose how to paint
├── TouchCanvasView.swift            # Finger / Apple Pencil canvas
├── CreationCanvas.swift             # AR painting canvas
├── MuseumStore.swift                # Persistence and session state
├── MuseumWallView.swift             # Personal gallery
├── MuseumWallBackground.swift       # Gallery background rendering
├── ArtworkDetailSheet.swift         # Artwork detail / edit / share / delete
├── ProfileSheet.swift               # Profile, stats, badges, settings
├── Badges.swift                     # Achievement system
├── SoundManager.swift               # Sound effects
├── Localization+AppLanguage.swift   # In-app language switching
├── Color+Hex.swift                  # Brand color definitions
├── ColorMath.swift                  # Color blending utilities
├── FontExtension.swift              # Custom font (Fredoka) registration
├── CodedPictureFrames.swift         # Frame rendering
├── FrameStyle.swift                 # Frame style definitions
├── SpotlightsView.swift             # Decorative spotlight animations
├── en.lproj / it.lproj             # Localized strings
└── AnimationExtensions/             # Confetti, button styles, small animations
```

## Privacy

There are no accounts, no sign-in, and no analytics. Everything a child creates, paintings, photos, progress, stays on the device.

## License

All Rights Reserved. This repository is a portfolio overview only, the project's source code is maintained in a private repository.
