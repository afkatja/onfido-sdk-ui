# Change Log
All notable changes to this project will be documented in this file.
This project adheres to the Node default version scheme, meaning It's safe to use with the caret ^ dependency definition.
The standard for the caret can [be found here](https://docs.npmjs.com/misc/semver#caret-ranges-123-025-004).
Breaking changes result in a different major. UI changes that might break customizations on top of the sdk, will be treated as breaking changes too.


## [new-version]

### Added
- Public: An error message is now shown if the upload file has as unsupported file type.


## [0.8.1]

## Fixed
- `Object.assign` was being used but not polyfilled. Its occurrence was replaced with an es6 object construction.
- UI disappeared if the browser's windows width was smaller than 481px;


## [0.8.0]

### Changed
- Public: Captures are now returned as `png` instead of `webp`, although `webp` is still used internally for streaming to the server.
- Public: the captures returned by `Onfido.getCaptures()` have a simplified signature of just `{id,image,documentType}`.
- Public: It's now possible to open and close the modal by calling `.setOptions({isModalOpen:boolean})`
- Internal: The modal has been refactored to be fully reactive, `vanilla-modal` has been replaced with a fork of `react-modal`.
- Internal: Updated to `onfido-sdk-core@0.6.0`, selectors are now more general as in they are no longer specific to each capture type, some new selectors are also being used.
- Internal: `Camera`, `Capture` and `Uploader` have been refactored, the pure part of the components have been separated from the state logic part. This adds flexibility and encapsulation.
- Internal: The `Capture` component now orchestrates all the state logic of the `Uploader` component, this allows to join the camera and uploader state logic together.

### Added
- Public: The capture screen UI now includes an upload button fallback, for whenever the user experiences problems with the webcam.
- Internal: When requesting to validate documents there is now a strategy to cope with slow responses from the server. If the number of unprocessed documents is 3+, the client stops sending more requests until a response is given.
- Internal: `webp` falls back to `jpeg` in case the browser does not support it.


## [0.7.0]

### Changed
- Public: `onComplete` event now fires only after both the document and face captures have been confirmed in the UI
- Internal: updated `onfido-sdk-core` to 0.5.0 which causes the all capture event to be triggered when captured are both valid and confirmed
- Internal: made the confirm button change the state of the capture to confirmed

### Fixed
- Internal: sometimes when document was retaken multiple times the capture ended up squashed. This was fixed by upgrading to `react-webcam@0.0.14`.
- Internal: fixed [Bug #36](https://github.com/onfido/onfido-sdk-ui/issues/36), it caused the face to be captured every second after a document retake.


## [0.6.1]

### Changed
- Public: `Onfido.init()` now returns an object.
- Internal: `isDesktop` detection is now based on [DetectRTC][detectrtc]'s `isMobile` detection
- Internal: improved Webcam Detection, it now takes into account wether a Webcam exists and if it the user has given the website permission to use it. Before it was only checking whether the **getUserMedia** API is supported by the browser or not. [DetectRTC][detectrtc] is used for this detection.

### Added
- Public: it's now possible to change the init options at runtime by calling `setOptions()` on the object returned by `Onfido.init()`
- Public: `useWebcam` option added to the facial and document capture step

[detectrtc]: https://github.com/muaz-khan/DetectRTC


## [0.5.1]
### Fix
- SDK Core dependency update, fixes issue https://github.com/onfido/onfido-sdk-ui/issues/25
**Note:** This update only changes the dist folder release, npm releases get the dependency update if they do `npm install`


## [0.5.0]
### Added
- API: Flow customization option `steps:[]`
- UI: Overlay to the webcam document capture (**Possibly breaking change**)
- DOC: Integration examples to documentation
### Fixed
- NPM (commonjs2) style of importing the library now works


The standard for this change log can be found [here](http://keepachangelog.com/).

[new-version]: https://github.com/onfido/onfido-sdk-ui/compare/0.8.0...master
[0.8.1]: https://github.com/onfido/onfido-sdk-ui/compare/0.8.0...0.8.1
[0.8.0]: https://github.com/onfido/onfido-sdk-ui/compare/0.7.0...0.8.0
[0.7.0]: https://github.com/onfido/onfido-sdk-ui/compare/0.6.1...0.7.0
[0.6.1]: https://github.com/onfido/onfido-sdk-ui/compare/0.5.1...0.6.1
[0.5.1]: https://github.com/onfido/onfido-sdk-ui/compare/0.5.0...0.5.1
[0.5.0]: https://github.com/onfido/onfido-sdk-ui/compare/0.4.0...0.5.0