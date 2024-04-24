# Pear Runtime Codebase Overview (as of April 24, 2024)

This document provides a comprehensive overview of the Pear Runtime codebase, highlighting key components and their functionalities.

## Core Components:

    ./gui.js & ./preload.js:

        Manage the graphical user interface (GUI) of Pear applications using Electron.

        Handle window creation, management, and communication between the renderer process and the main process.

    ./ctx directory:

        Contains context classes (shared.js, sidecar.js) that manage application and platform configurations.

        Provides methods to update and access application metadata, options, and state.

    ./lib directory:

        Houses various utility functions and modules:

            ./lib/applings.js: Manages application registration and association with executable files.

            ./lib/bundle.js: Handles application bundles, including loading, updating, and tracing.

            ./lib/constants.js: Defines constants used throughout the codebase (paths, keys, etc.).

            ./lib/crasher.js: Sets up crash handlers to log unhandled errors and rejections.

            ./lib/gunk.js: Provides configuration for the script linker, managing builtins and module resolution.

            ./lib/iface.js: Offers utility functions for command-line interface (CLI) interactions and output formatting.

            ./lib/mime.js: Handles MIME type detection for files.

            ./lib/parse.js: Parses command-line arguments and extracts relevant information.

            ./lib/preferences.js: Manages application preferences and persistent storage.

            ./lib/release-watcher.js: Watches for application release updates.

            ./lib/reports.js: Defines report formats for different error and status scenarios.

            ./lib/replicator.js: Handles replication and peer-to-peer communication using Hypercore Protocol.

            ./lib/run.js: Executes Pear applications, managing processes and communication.

            ./lib/sidecar.js: Implements the Sidecar server, responsible for serving application bundles and handling IPC communication.

            ./lib/stdio.js: Provides abstractions for standard input/output interactions.

            ./lib/subsystem.js: Loads and manages subsystems from Hyperdrives.

            ./lib/teardown.js: Handles application teardown and graceful shutdown.

            ./lib/tracer.js: Traces application execution for warmup optimization.

            ./lib/tryboot.js: Attempts to start the Sidecar process.

            ./lib/url-handler.js: Registers URL handlers for Pear protocols on different operating systems.

## CLI Commands (./cmd directory):

    ./cmd/init.js: Implements the pear init command.

    ./cmd/dev.js: Implements the pear dev command.

    ./cmd/stage.js: Implements the pear stage command.

    ./cmd/seed.js: Implements the pear seed command.

    ./cmd/release.js: Implements the pear release command.

    ./cmd/run.js: Implements the pear run and pear launch commands.

    ./cmd/info.js: Implements the pear info command.

    ./cmd/dump.js: Implements the pear dump command.

    ./cmd/sidecar.js: Implements the pear sidecar command.

## API Functions (./lib/api.js):

    message(msg): Sends a message to the Pear platform.

    messages(pattern, listener): Subscribes to messages matching a specific pattern.

    checkpoint(state): Stores application state as a checkpoint.

    versions(): Retrieves version information for the platform and application.

    restart(opts): Restarts the application or platform.

    updates(listener): Subscribes to application update events.

    wakeups(listener): Subscribes to application wakeup events.

    teardown(fn): Registers a function to be executed during application teardown.

    exit(code): Exits the application with the specified exit code.

Additional Notes:

    The ./test directory contains unit tests for various components.

    The ./examples directory provides sample Pear applications.