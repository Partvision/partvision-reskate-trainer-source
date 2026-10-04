# Partvision ReSkate Trainer 0.4.0 preview 6

Use a Visual Studio x64 Developer Command Prompt with C++ tools, Windows SDK, CMake and Ninja.

```bat
cmake -S . -B build/early -G Ninja -DCMAKE_BUILD_TYPE=Release -DDINGOSDK_VERSION=1.0.6 -DDINGOSDK_BUILD_MULTIPLAYER_TESTS=ON
cmake --build build/early --target dingosdk_runtime dingosdk_launcher early_trainer_check early_trainer_logic_check early_trainer_ui_check dingosdk_physics_tuning_tests -j 4
build\early\early_trainer_check.exe "C:\Program Files (x86)\Steam\steamapps\common\Skate"
build\early\early_trainer_logic_check.exe
build\early\early_trainer_ui_check.exe
build\early\dingosdk_physics_tuning_tests.exe "C:\Program Files (x86)\Steam\steamapps\common\Skate"
```

Build inside the source tree; upstream source_group expects this. The runtime and launcher use the 1.0.6 base version; the trainer displays 0.4.0-preview6.

The UI test uses a separate ImGui library with assertions enabled. It defaults to Arial from C:/Windows/Fonts; an optional directory argument exports Home and Player draw geometry for layout inspection.

Main new code: Extension/EarlyTrainer. See packaging/README.md for behavior, limitations and source attribution. UI callbacks only edit preferences; the game thread owns native edits. Native debug requests pass through the existing request scheduler. Source includes the changes to no_bail/client_noclip/offboard_flight that provide state sampling and off-board jump scaling. Pending jump scaling is guarded against concurrent native updates and may be canceled.

The source and installer scripts are GPL-3.0; see LICENSE.
