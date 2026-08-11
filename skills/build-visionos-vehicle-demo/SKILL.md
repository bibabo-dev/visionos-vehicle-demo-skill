---
name: build-visionos-vehicle-demo
description: Build an Apple Vision Pro vehicle showcase and immersive cockpit experience from a user-supplied 3D vehicle model. Use when Codex needs to inspect, normalize, split, optimize, export, and integrate a Blender or USDZ vehicle asset into a SwiftUI and RealityKit visionOS project with a mixed-reality welcome model, immersive cabin placement, gaze and pinch interactions, spatial audio, startup sequences, and device validation.
---

# visionOS Vehicle Demo Builder

Build a reusable Apple Vision Pro vehicle experience from a user-supplied model.

## Required inputs

Ask the user for:

- Vehicle model in BLEND, FBX, GLTF, GLB, OBJ, or USDZ format
- Texture files
- Interior and exterior reference photographs
- Target visionOS version
- Interaction requirements
- Audio files
- Licensing information for all supplied assets

Do not redistribute user-supplied or third-party models without permission.

## Workflow

1. Inspect the existing project and report its current state before changing files.
2. Preserve user changes and create a Git checkpoint before risky modifications.
3. Inspect the vehicle model, textures, dimensions, hierarchy, and coordinate system.
4. Normalize the Blender scene to meters and apply transforms.
5. Place the vehicle root at a documented origin.
6. Separate interactive parts into clearly named entities.
7. Create simple invisible hit areas for small interactive parts.
8. Export an optimized USDZ asset for RealityKit.
9. Build a mixed-reality welcome scene with a rotatable miniature vehicle.
10. Build a 1:1 immersive cockpit scene.
11. Calibrate the seated eye position using the real vehicle geometry.
12. Implement gaze and pinch interactions with RealityKit components.
13. Implement spatial audio, lighting, environmental imagery, and state machines.
14. Validate in the visionOS Simulator and, when available, on Apple Vision Pro.
15. Record configuration values and create a rollback checkpoint.

## Recommended entity structure

Use semantic names rather than Blender-generated names:

- Vehicle_Root
- Exterior
- Interior
- SteeringWheel
- Horn
- IgnitionKey
- ClutchPedal
- BrakePedal
- AcceleratorPedal
- GearLever
- HandBrake
- InteractionZones

Interactive entities should have:

- A correct rotation pivot
- Applied transforms
- A documented movement range
- A low-complexity collision proxy
- A semantic RealityKit identifier

## RealityKit architecture

Prefer modular files for:

- Scene and asset loading
- Vehicle configuration
- Interaction components
- Gesture systems
- Experience state machines
- Audio management
- Placement calibration

Use `CollisionComponent`, `InputTargetComponent`, and `HoverEffectComponent` only on intended targets or dedicated invisible hit areas.

## Validation

Before reporting completion:

- Confirm the model is visible in both scenes
- Confirm scale and eye position
- Confirm textures and lighting
- Confirm all collision proxies are invisible at runtime
- Confirm interaction order and state transitions
- Confirm spatial audio positions
- Confirm the user can exit the immersive space
- Preserve a rollback point