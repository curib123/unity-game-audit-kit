# Official Unity reference starting points

Use the documentation for the **version actually recorded in the target project**. The links below are verified Unity 6.0 reference examples, not a recommendation to upgrade or an assumption that the game uses that version. Choose the matching version in Unity's documentation before applying API or configuration details.

| Audit subject | Official reference | How to use it |
| --- | --- | --- |
| Build configuration and per-profile scene lists | [Build Profiles window reference](https://docs.unity3d.com/6000.0/Documentation/Manual/build-profiles-reference.html) | Check the actual active profile and applicable overrides. Do not infer every build's scenes from one global list. |
| Asset identity and import metadata | [Asset metadata](https://docs.unity3d.com/6000.0/Documentation/Manual/AssetMetadata.html) | Understand asset IDs and associated metadata before assessing broken references or recommending asset moves/removals. |
| Configurable Play Mode behavior | [EnterPlayModeOptions API](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/EnterPlayModeOptions.html) | Interpret the detected domain/scene reload configuration. Inspect behavior under the project's actual settings rather than changing them during an audit. |
| Performance evidence | [Unity Profiler](https://docs.unity3d.com/6000.0/Documentation/Manual/Profiler.html) | Plan appropriate captures and identify their environment. Tie performance conclusions to measurements, not a generic code checklist. |
| Reusable authored objects | [Prefabs](https://docs.unity3d.com/6000.0/Documentation/Manual/Prefabs.html) | Assess prefab composition and reuse in the existing project; preserve appropriate variants and overrides. |
| Shared data assets | [ScriptableObject data assets](https://docs.unity3d.com/6000.0/Documentation/Manual/class-ScriptableObject.html) | Consider shared configuration where it has a real purpose, with deliberate runtime state ownership. |
| Existing UI Toolkit authoring | [UI Builder](https://docs.unity3d.com/6000.0/Documentation/Manual/UIBuilder.html) | Use matching UXML/USS authoring guidance when the project uses UI Toolkit; this is not a reason to migrate another UI system. |

For packages such as an input system, render pipeline, networking framework, Addressables, or a test framework, first identify the installed package and version in the game. Then use that package's matching official documentation. The kit intentionally has no dependency on a particular renderer, networking stack, or Unity version.

These sources explain engine behavior; they do not establish findings about a game. A report still needs evidence from the actual target project and the configuration being assessed.
