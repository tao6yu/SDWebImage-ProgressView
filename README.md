# SDWebImage-ProgressView
Category on UIImageView, adding a progress view while images are downloaded using SDWebImage.


## Installation
Use [Cocoapods](http://cocoapods.org):

```
pod 'SDWebImage-ProgressView'
```


## Usage
All of SDWebImage's UIView+WebCache methods gained an extra parameter:

```
- (void)setImageWithURL:(NSURL *)url usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder options:(SDWebImageOptions)options usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url completed:(SDWebImageCompletedBlock)completedBlock usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder completed:(SDWebImageCompletedBlock)completedBlock usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder options:(SDWebImageOptions)options completed:(SDWebImageCompletedBlock)completedBlock usingProgressView:(UIProgressView *)progressView;
- (void)setImageWithURL:(NSURL *)url placeholderImage:(UIImage *)placeholder options:(SDWebImageOptions)options progress:(SDWebImageDownloaderProgressBlock)progressBlock completed:(SDWebImageCompletedBlock)completedBlock usingProgressView:(UIProgressView *)progressView;
```

Use `nil` for the `progressView` parameter to use the system default `UIProgressView`, or provide your own progress view (or subclass thereof) if you want custom styling and tint colors.

If you're using the `cancelCurrentImageLoad` method, you'll also have to call `removeProgressView` or you'll end up with lingering progress views.

```
- (void)prepareForReuse {
    [super prepareForReuse];
    [self.imageView cancelCurrentImageLoad];
    [self.imageView removeProgressView];
}
```


## License
SDWebImage-ProgressView is available under the MIT license. See the LICENSE file for more info.