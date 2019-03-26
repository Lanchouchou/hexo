---
title: doctor J
date: 2019-03-25 14:16:51
tags:
---
{% codeblock %}
render () {
    const { selectedSizeList } = this.props
    const maxSizes = getMaxSizes(selectedSizeList)
    return (
      <section
        className={classNames(
          commonStyles.section,
          styles.fileConfig,
          'pd-intel-file-config'
        )}
      >
        <div className="us-section">
          {!!maxSizes.length && (
            <div className={styles.uploadTips}>
              根据您选择的尺寸包，您需上传以下尺寸的 PSD 文件
            </div>
          )}
          <div className={classNames('us-section-main', styles.isFlex)}>
            {!maxSizes.length && (
              <Uploader disabled style={{ cursor: 'no-drop' }} />
            )}
            {map(maxSizes, size => (
              <Uploader
                key={`${size[0] * size[1]}`}
                size={size}
                onUploaded={this.onUploaded}
              />
            ))}
          </div>
        </div>
      </section>
    )
  }
}
{% endcodeblock %}