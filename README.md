[![GitHub license](https://img.shields.io/github/license/smdn/Smdn.Extensions.Polly)](https://github.com/smdn/Smdn.Extensions.Polly/blob/main/LICENSE.txt)
[![tests/main](https://img.shields.io/github/actions/workflow/status/smdn/Smdn.Extensions.Polly/test.yml?branch=main&label=tests%2Fmain)](https://github.com/smdn/Smdn.Extensions.Polly/actions/workflows/test.yml)
[![CodeQL](https://github.com/smdn/Smdn.Extensions.Polly/actions/workflows/codeql-analysis.yml/badge.svg?branch=main)](https://github.com/smdn/Smdn.Extensions.Polly/actions/workflows/codeql-analysis.yml)

# Smdn.Extensions.Polly

This repository provides libraries that extend the features of [Polly](https://github.com/App-vNext/Polly).

> [!NOTE]
> This repository was extracted from [`smdn/Smdn.Fundamentals`](https://github.com/smdn/Smdn.Fundamentals). Due to the historical repository split, the git commit log may contain unrelated historical commits from the original repository.



## Smdn.Extensions.Polly.KeyedRegistry
[![NuGet](https://img.shields.io/nuget/v/Smdn.Extensions.Polly.KeyedRegistry.svg)](https://www.nuget.org/packages/Smdn.Extensions.Polly.KeyedRegistry/)

Polly.Extensions enables the registration of a `ResiliencePipeline` into the DI container with a specified key via the `AddResiliencePipeline` method. In this approach, Polly.Extensions registers a `ResiliencePipelineProvider` for each key type.

**Smdn.Extensions.Polly.KeyedRegistry** enables `ResiliencePipelineProvider` itself to be registered as a keyed service. To achieve this, the library introduces the `IResiliencePipelineKeyPair<TServiceKey, TPipelineKey>` interface and overload methods of `AddResiliencePipeline` for registering a `ResiliencePipeline` using `TServiceKey` and `TPipelineKey` as keys. Keyed `ResiliencePipelineProvider` instances registered through these mechanisms can be retrieved via `GetRequiredKeyedService<ResiliencePipelineProvider<TPipelineKey>>(TServiceKey)`.

Consequently, `ResiliencePipeline` instances added to the DI container via this mechanism are registered hierarchically as a pair of two keys: `TServiceKey` as the upper-level key designating the target `ResiliencePipelineProvider`, and `TPipelineKey` as the lower-level key representing the `ResiliencePipeline` registered within that provider.



# For contributors
Contributions are appreciated!

If there's a feature you would like to add or a bug you would like to fix, please read [Contribution guidelines](./CONTRIBUTING.md) and create an Issue or Pull Request.

IssueやPull Requestを送る際は、[Contribution guidelines](./CONTRIBUTING.md)をご覧頂ください。　可能なら英語が望ましいですが、日本語で構いません。

# Notice
<!-- #pragma section-start NupkgReadmeFile_Notice -->
## License
This project is licensed under the terms of the [MIT License](./LICENSE.txt).

## Credits
This project uses the following components. See [ThirdPartyNotices.md](./ThirdPartyNotices.md) for detail.

- [App-vNext/Polly](https://github.com/App-vNext/Polly)

<!-- #pragma section-end NupkgReadmeFile_Notice -->
