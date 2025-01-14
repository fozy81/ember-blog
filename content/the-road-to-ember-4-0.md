---
title: The Road to Ember 4.0
authors:
  - matthew-beale
date: 2021-07-14T00:00:00.000Z
tags:
  - roadmap
  - '2021'
---

Contributors to the Ember project have been hard at work since [Ember Octane](https://blog.emberjs.com/octane-is-here/) was released in December 2019.

Over the duration of a challenging (and sometimes devastating) year and a half, we've shipped a powerful new feature ([Named Blocks](https://api.emberjs.com/ember/3.26/modules/@glimmer%2Fcomponent#passing-multiple-blocks)) and supported an ecosystem shifting to Octane conventions. We've more closely aligned Ember with wider frontend conventions through improved publishing & build tooling ([Embroider](https://github.com/embroider-build/embroider)) and better support for TypeScript (both through [ember-cli-typescript](https://github.com/typed-ember/ember-cli-typescript) and reducing reliance on type-unsafe framework features).

Check out [Godfrey's EmberConf 2021 keynote](https://youtu.be/1Z6cLV2licU?t=103) for
a more complete walk-through of recent changes in Ember.

## Announcing Ember 4.0

In his [EmberConf 2021 keynote](https://www.youtube.com/watch?v=pJPUQQQ9QDg), Yehuda shared a name for Ember's next edition: **Polaris**. In order to unblock Polaris providing the best, most productive experience the Ember project can build, we're going to remove already-deprecated APIs in a 4.0 release.

Ember 3.27, which has already been released, was the final version of Ember to include new deprecations targeting Ember 4.0.

Ember 3.28, which has been released as a beta, will be released as stable around August 9th. It will not introduce additional deprecations targeting Ember 4.0. Six weeks after its stable release, around September 20th, Ember 3.28 will become a [Long-Term Support](https://emberjs.com/releases/lts/) release.

**Ember 4.0 will be released around September 20th.** Ember 4.0 itself is not an LTS candidate.

Ember 4.4 will be the first LTS candidate of the 4.x series. It will be released as stable around February 2022 and as an LTS around March 2022.

## Whats in a 4.0?

Since the release of Ember 2.0, major versions of Ember have been about removal of deprecated API, and not about the introduction of new features or development styles. **Ember 4.0 follows that tradition, and will contain no new features.**

Additionally, Ember 4.0 does not remove the `EmberComponent` API or the core parts of the `EmberObject` system. These APIs are widely used, even after the release of Octane, by existing application and addon code.

Ember 4.0 will remove [all APIs deprecated in Ember 3.x](https://deprecations.emberjs.com/v3.x) and targeting Ember 4.0. These include:

- `Ember.Logger` is removed in favor of native `console` APIs. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-console-deprecate-logger).
- `Copyable` mixin is removed in favor of the [ember-copy addon](https://github.com/emberjs/ember-copy). [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-runtime-deprecate-copy-copyable).
- `sendAction` is removed in favor of calling closure actions like any other callback. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-component-send-action).
- `willTransition` and `didTransition` are removed in favor of router service events. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_deprecate-router-events).
- Computed Property `volatile()` calls are removed in favor of native getters. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_computed-property-volatile).
- `this.$()` and other jQuery APIs are deprecated in favor of native browser equivalents. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_jquery-apis). An optional feature which restored this and other jQuery-specific features is also removed. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_optional-feature-jquery-integration).
- `{{partial}}` is removed in favor of template-only components. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-partial).
- Using the built-in global resolver (`App.FooController` anyone?) is deprecated in favor of using [ember-resolver](https://github.com/ember-cli/ember-resolver), already the default for Ember CLI generated apps. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-deprecate-globals-resolver).
- Ambiguous references to a component's properties are removed. You must now write `{{this.someProp}}`. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_this-property-fallback).
- `renderTemplate` is removed in favor of `{{in-element}}` or other rendering target redirection like [ember-wormhole](https://github.com/yapplabs/ember-wormhole). [Guide here](https://deprecations.emberjs.com/v3.x/#toc_route-render-template).
- Support for the `Ember` global on `window` is removed in favor of importing the `Ember` object or using the module-based API. [Guide here](https://deprecations.emberjs.com/v3.x/#toc_ember-global).
- Support for specific features of the `<LinkTo>`, `<Input>`, and `<Textarea>` components are removed. See guides on [positional arguments](https://deprecations.emberjs.com/v3.x/#toc_ember-glimmer-link-to-positional-arguments), [legacy arguments](https://deprecations.emberjs.com/v3.x/#toc_ember-built-in-components-legacy-arguments), [legacy HTML attributes](https://deprecations.emberjs.com/v3.x/#toc_ember-built-in-components-legacy-attribute-arguments), and [importing legacy built-in components](https://deprecations.emberjs.com/v3.x/#toc_ember-built-in-components-import).
- Finally, **Ember classic is deprecated in favor of Ember Octane**. Although
many APIs from Ember classic (like `EmberComponent`) continue to be available,
the optional features and application configuration which define Ember Octane
must be enabled in 4.0. See [the deprecation guide
entry](https://deprecations.emberjs.com/v3.x#toc_editions-classic) and
[upgrading to Ember
Octane](https://guides.emberjs.com/v3.27.0/upgrading/current-edition/) guide for
more details.

The above APIs, listed as an example of what will be removed but not defining the complete list, show that API removals in 4.x largely consist of APIs that date back to Ember 1.x, and are rarely used now (or should be rarely used).

An additional important change is the completion of Ember 3.x's browser support policy. Ember 4.0 will support two classes of browsers: Evergreen (those on a weeks-long, auto-upgrade release cycle) and non-evergreen. This classification system allows us to create a rolling minimum version for evergreen browsers, while using a more traditional, pinned minimum version for non-evergreen browsers.

**Specifically, the Ember 4.x release policy includes support for Google Chrome, Mozilla Firefox, Microsoft Edge, and Apple Safari on desktop and mobile. It does not include support for any version of Internet Explorer.**

Read more about this change in [the deprecation guide](https://deprecations.emberjs.com/v3.x/#toc_3-0-browser-support-policy) and at [Ember's browser support policy page](https://emberjs.com/browser-support/).

Existing Ember users should note that Ember 3.27 has already removed IE11 from the default target list for production and testing builds.

## Planning your upgrade to 4.0

For each API removed in Ember 4.0, you can find an entry in the [Ember 3.x deprecation guide](https://deprecations.emberjs.com/v3.x/). As many of the removed APIs have not been included in best practices or common documentation for the entire 3.x cycle, applications started on 3.x are expected to have a fairly smooth upgrade path.

Consider using the [ember-cli-deprecation-workflow](https://github.com/mixonic/ember-cli-deprecation-workflow) addon as part of your upgrade process. The addon allows you to create a configuration file to silence most deprecations. This means you can focus on one or a few warnings at a time. Additionally, you can configure the addon to throw an error when a deprecation that was previously addressed is re-introduced. If you work with a large codebase and many contributors, this helps you prevent backsliding in your upgrade process.

In contrast to prior major releases, we have no plans to offer an
`ember-3-legacy` package that makes Ember 3.x APIs available for a limited time
in Ember 4.0. This is based on fairly low use of these packages in the past.

**Don't panic.** We expect many Ember users to enthusiastically adopt our 4.0 release. If you prefer a conservative upgrade path, we suggest using Ember's Long-Term Support releases. Ember 3.28, the last version of the 3.x cycle, will become an LTS in September 2021. The first 4.x release to be promoted to LTS will be Ember 4.4 around March 2022. This timeline provides a long window for your business to address any remaining 4.0-targeted deprecations (while using 3.28-LTS) before 4.4-LTS is promoted.

## Contributing to Ember 4.0

In the [Ember.js](https://github.com/emberjs/ember.js), [Ember Data](https://github.com/emberjs/data), and [Ember CLI](https://github.com/ember-cli/ember-cli) repos, the final beta cycle of 3.x has already started. The `master` branch is ready for code changes targeting 4.0. You are welcome to contribute to these repos by removing already deprecated functionality and IE11 compatibility code.

The core framework effort to prepare for 4.0 is tracked at
[emberjs/ember.js#19545](https://github.com/emberjs/ember.js/issues/19545), and
a list of deprecated APIs we need help to remove is tracked at
[emberjs/ember.js#19617](https://github.com/emberjs/ember.js/issues/19617).

Join us on [Discord](https://discord.com/invite/emberjs) in the `#dev-ember-js`, `#dev-ember-data`, `#dev-ember-cli`, or `#dev-ember-learning` channels to find out how you can contribute.

In less than six weeks, we expect the first betas for 4.0 to be released. Please help test the betas on your applications and addons so that we can catch any regressions.

We're looking forward to working with the community on Ember 4.0 and on the opportunities beyond it. As always we appreciate your support, your trust, and our common partnership.
