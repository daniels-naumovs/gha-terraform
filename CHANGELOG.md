# Changelog

## [3.0.0](https://github.com/workivate/daniels-naumovs-terraform/compare/v2.1.0...v3.0.0) (2022-09-02)


### ⚠ BREAKING CHANGES

* removed `inputs.step` default value

### Features

* removed `inputs.step` default value ([9b369ca](https://github.com/workivate/daniels-naumovs-terraform/commit/9b369cafb96895ada4e5145eb73a155fbd4b26ab))

## [2.1.0](https://github.com/workivate/daniels-naumovs-terraform/compare/v2.0.0...v2.1.0) (2022-06-09)


### Features

* added `force-unlock` ([58656d2](https://github.com/workivate/daniels-naumovs-terraform/commit/58656d2396ec3342efe0463943976e376017bf8a))


### Bug Fixes

* inject `inputs.TF_CLI_ARGS_force-unlock` directly into `run` ([e171201](https://github.com/workivate/daniels-naumovs-terraform/commit/e171201b9c3713c2220dddc4722ac9ce8d4cf9f5))

## [2.0.0](https://github.com/workivate/daniels-naumovs-terraform/compare/v1.0.0...v2.0.0) (2022-06-07)


### ⚠ BREAKING CHANGES

* **general:** removed `inputs.account-alias` and `step.id.aws-account-metadata` AWS-specific steps
* **general:** made action provider-ambiguous

### Features

* **cli:** added the ability to run the action with a custom version of Terraform ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))
* **cli:** made all `TF_CLI_ARGS_*` environment variables customizable as inputs ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))
* **destroy:** changed `terraform apply -destroy` to `terraform destroy` for backwards compatibility with `v0.15.2` and older versions of Terraform ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))
* **general:** made action provider-ambiguous ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))
* **general:** removed `inputs.account-alias` and `step.id.aws-account-metadata` AWS-specific steps ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))


### Bug Fixes

* **fmt:** removed the `continue-on-error` option for the `fmt` step ([dece440](https://github.com/workivate/daniels-naumovs-terraform/commit/dece440d32e9005694fc5abe70e46aa24dfb6b73))
* **inputs:** removed unused input `repository-name` ([4a2f212](https://github.com/workivate/daniels-naumovs-terraform/commit/4a2f212e0df2a230cf6bb8a5ee942e80068adfe0))
* **inputs:** removed unused input `token` ([59559d7](https://github.com/workivate/daniels-naumovs-terraform/commit/59559d75c9cf43f7f26ed9940a6c44ae408286ae))

## 1.0.0 (2022-05-31)


### Features

* added `destroy` functionality ([3d44c09](https://github.com/workivate/daniels-naumovs-terraform/commit/3d44c094b58ea15715809a5d6e1d45dd03167d1f))
* added `import` functionality ([54fbe86](https://github.com/workivate/daniels-naumovs-terraform/commit/54fbe864d047f8e2c9fc7ed86ccc453ed21a0ee4))
* added `release-please` ([b2a5926](https://github.com/workivate/daniels-naumovs-terraform/commit/b2a592636ed48db508e7e3d4bb8befa03d770b95))
* added initial Action ([6c1a739](https://github.com/workivate/daniels-naumovs-terraform/commit/6c1a739b952b5aaa6df7f05ef82bdb49496e3952))


### Bug Fixes

* added `--auto-approve` to avoid hanging ([4ebc364](https://github.com/workivate/daniels-naumovs-terraform/commit/4ebc3646b52d2fa804a64370f1e267b52802f009))
* added token for pulling util repos ([416b7c4](https://github.com/workivate/daniels-naumovs-terraform/commit/416b7c4973903b039aa84eca06ad3ddb03d22e9a))
* added varfile and workdir support, added step conditions ([e2cead0](https://github.com/workivate/daniels-naumovs-terraform/commit/e2cead0f58b6772fd34abcbaa63574f1d8fc45bc))
* added vars to `destroy` command ([e376e09](https://github.com/workivate/daniels-naumovs-terraform/commit/e376e09813abac99e6a9c28dc903a535e483c6e3))
* corrected array syntax ([1bb0cba](https://github.com/workivate/daniels-naumovs-terraform/commit/1bb0cba5d51c0d910ca9018e2b5e8dfdb24b07c4))
* indentation ([e9dd2a2](https://github.com/workivate/daniels-naumovs-terraform/commit/e9dd2a2b237c3e0871e186529f0dce3a45d3faf1))
* **input:** fixed more `inputs` ([1537258](https://github.com/workivate/daniels-naumovs-terraform/commit/153725853c2529417b566f4c2a989dbb0a91c51e))
* set correct `var-file` path ([bf7768f](https://github.com/workivate/daniels-naumovs-terraform/commit/bf7768fca855c9a92776d1c426a391a38437822f))
* **token:** re-added token, fixed `inputs` syntax ([45ad5d6](https://github.com/workivate/daniels-naumovs-terraform/commit/45ad5d6dd9ff2f64873c0aa26ca8b66d51c08aad))
