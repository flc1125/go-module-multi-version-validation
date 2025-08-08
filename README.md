# Go Module Multi-Version Validation

This is a validation reference used to verify the release of multiple versions based on the v0.x version.

## Overview

This project demonstrates how to properly implement Go module versioning with multiple major versions in a single repository. It serves as a reference implementation for validating Go module multi-version release strategies, particularly focusing on v0.x version handling and the transition to v2+ versions.

## Verification result

**Even if a v0.x version is released for v2, the actual application of v2 will still default to module management under the v2.x version.**

```go
package go_module_multi_version_validation

import (
	"testing"

	v0 "github.com/flc1125/go-module-multi-version-validation"
	v2 "github.com/flc1125/go-module-multi-version-validation/v2"
)

func TestHello(t *testing.T) {
	v0.Hello()
	v2.Hello()
}
```

```shell

❯ go mod graph | grep 'go-module-multi-version-validation'
golangdemo github.com/flc1125/go-module-multi-version-validation@v0.0.1
golangdemo github.com/flc1125/go-module-multi-version-validation/v2@v2.0.0-20250808052249-b9565a62f023
github.com/flc1125/go-module-multi-version-validation@v0.0.1 go@1.24.5
github.com/flc1125/go-module-multi-version-validation/v2@v2.0.0-20250808052249-b9565a62f023 go@1.24.5
```
