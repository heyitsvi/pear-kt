# CLI Commands:

    pear init [dir] (./init.js):

        Creates initial project files for a Pear application within the specified directory (defaults to current directory).

        Options:

            --yes|-y: Auto-selects all default options.

            --type|-t=type: Specifies project type (desktop or terminal).

            --force|-f: Overwrites existing files.

            --with|-w=name: Includes additional functionality (e.g., node).

    pear dev [flags] [dir] [...app-args] (./run.js):

        Runs a Pear project in development mode (equivalent to pear run --dev <dir>).

        Options:

            --link=url: Simulates a deep-link click open.

            --store|-s=path: Sets the Application Storage path.

            --tmp-store|-t: Creates a temporary folder for application storage.

    pear stage <channel|key> [dir] (./stage.js):

        Synchronizes local project changes to a specified channel or key.

        If using a channel for the first time, a new key will be generated.

        Options:

            --json: Outputs information in newline-delimited JSON format.

            --dry-run|-d: Performs a stage without writing changes.

            --bare|-b: Stages only file data, excluding warmup optimization.

            --ignore: Specifies files to ignore during staging (comma-separated list).

            --name: Overrides the application name.

    pear release <channel|key> (./release.js):

        Marks a specific version within a channel or key as the production release.

        Options:

            --json: Outputs information in newline-delimited JSON format.

            --checkout=n: Sets the checkout point to a specific version length.

    pear info [key] (./info.js):

        Displays information about a Pear project.

        If no key is provided, it shows general Pear information.

        Options:

            --json: Outputs information in newline-delimited JSON format.

    pear dump <key> <dir> (./dump.js):

        Downloads files from a specified key to a local directory.

        Options:

            --json: Outputs information in newline-delimited JSON format.

            --checkout=n: Dumps files from a specific checkout version.

    pear run [flags] <key|dir|alias> [...app-args] (./run.js):

        Runs a Pear application from a key, directory, or alias.

        Options:

            --dev: Enables development mode, including devtools and updates diff.

            --devtools: Opens devtools with the application (Desktop only).

            --updates-diff: Enables diff computation for the Pear.updates API.

            --no-updates: Disables updates triggered by the Pear.updates API.

            --link=url: Simulates a deep-link click open.

            --store|-s=path: Sets the application storage path.

            --tmp-store|-t: Uses a temporary folder for application storage.

            --checkout=n: Runs a specific checkout version.

            --no-ask-trust: Exits instead of prompting to trust unknown keys.

            --detached: Attempts to wake up an existing app instance or runs detached.

    pear seed <channel|key> [dir] (./seed.js):

        Seeds a Pear project or reseeds an existing key.

        Options:

            --json: Outputs information in newline-delimited JSON format.

            --seeders|-s: Specifies additional public keys to seed from (comma-separated).

            --name: Overrides the application name.

            --verbose|-v: Provides additional output.

    pear sidecar (./sidecar.js):

        Advanced command to run the Pear Sidecar in the terminal.

        The Sidecar is a local HTTP and IPC server facilitating corestore access.

        Options:

            --mem: Enables memory mode, using a RAM-based corestore.

            --verbose: Provides additional output.

    pear versions (./usage.js):

        Outputs version information for Pear and its dependencies.

        Options:

            --json: Outputs information as a single JSON object.

# API Functions:

These functions are available within Pear applications and accessible through the Pear global object.

    Pear.versions() (./api/app.js):

        Returns an object containing version information for both the platform and the application.

    Pear.checkpoint(state) (./api/app.js):

        Stores the provided state object as a checkpoint for the application.

    Pear.message(msg) (./api/app.js):

        Sends a message to the Pear platform.

    Pear.messages(pattern, listener) (./api/app.js):

        Subscribes to messages matching the specified pattern and triggers the listener function when a matching message is received.

    Pear.restart(opts) (./api/app.js):

        Restarts the application with optional options.

    Pear.updates(listener) (./api/app.js):

        Subscribes to application update notifications and triggers the listener function when an update is available.

    Pear.wakeups(listener) (./api/app.js):

        Subscribes to application wake-up events and triggers the listener function when the application is woken up.

    Pear.teardown(fn) (./api/app.js):

        Registers a function to be executed when the application is shutting down.

    Pear.exit(code) (./api/app.js):

        Exits the application with the specified exit code.

Additional API functions (Desktop only) are accessible through Pear.Window and Pear.View objects:

    Pear.Window.self.focus(options): Focuses the main application window.

    Pear.Window.self.blur(): Blurs the main application window.

    Pear.Window.self.show(): Shows the main application window.

    Pear.Window.self.hide(): Hides the main application window.

    Pear.Window.self.minimize(): Minimizes the main application window.

    Pear.Window.self.maximize(): Maximizes the main application window.

    Pear.Window.self.fullscreen(): Makes the main application window fullscreen.

    Pear.Window.self.restore(): Restores the main application window from a minimized, maximized, or fullscreen state.

    Pear.Window.self.close(): Closes the main application window.

    Pear.Window.self.dimensions(options): Gets or sets the dimensions of the main application window.

    Pear.View.open(entry, options): Opens a new view within the application.

    Pear.View.close(id): Closes the view with the specified ID.

Deprecated API functions:

    Pear.preferences(): Access preferences functionality. This will be removed in September 2024.