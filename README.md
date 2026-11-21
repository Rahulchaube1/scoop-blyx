<img src="https://www.blyx-lang.space/blyx.png" width="90" alt="Blyx">

# Blyx Scoop bucket

Install the Blyx compiler and its native AI command-line tools on Windows x64. Each manifest names a release archive and pins its SHA-256 digest.

With [Scoop](https://scoop.sh/) installed, run these commands in PowerShell.

```powershell
scoop bucket add blyx https://github.com/Rahulchaube1/scoop-blyx
scoop install blyx/blyx blyx/blyxtorch blyx/linearfit blyx/residualwatch blyx/modelgate
blyxc --version
```

| Command | Input and use |
| --- | --- |
| `blyxc` | Run Blyx source or compile a native application with Rust and a host linker. |
| `blyxtorch` | Train a dense binary classifier or emit a custom Blyx network. [Training tutorial](https://doc.blyx-lang.space/guide/blyxtorch) |
| `linearfit` | Fit a one-feature regression from a CSV headed `x,y`. |
| `residualwatch` | Detect sustained errors in a chronological CSV headed `actual,predicted`. |
| `modelgate` | Compare two classifiers on a paired CSV headed `label,baseline,candidate`. |

For a first prediction, use the fixture installed alongside LinearFit.

```powershell
$sample = Join-Path (scoop prefix linearfit) 'fixtures/line.csv'
linearfit $sample --predict 5
```

The JSON report should show slope 2 and prediction 11. Use `scoop update` to refresh the manifests, followed by `scoop update linearfit` to install a newer version. The x64 tools use the Microsoft Visual C++ runtime. [Package catalog](https://www.blyx-lang.space/packages) · [Training and monitoring tutorial](https://doc.blyx-lang.space/guide/training-and-monitoring)

## Update a manifest

Use the public release URL and match its digest against the release’s SHA256SUMS. Check the executable name and archive layout. Run the Windows install workflow on a pull request and confirm the installed shim executes the supplied fixture. The compiler and tool sources are maintained in their own Blyx repositories.
