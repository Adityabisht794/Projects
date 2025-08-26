# Chat Analyzer

A Jupyter notebook-based tool for analyzing chat logs and group conversations. Perfect for WhatsApp exports, group chats, and other timestamped conversation formats.

## Features

- **📊 Message Analytics**: Count messages per user, daily activity patterns
- **⏰ Time Analysis**: Hourly heatmaps, weekday activity, timeline trends
- **📝 Content Analysis**: Top words, word frequency, content insights
- **🎨 Visualizations**: Bar charts, line graphs, heatmaps, word clouds
- **🔄 Multi-format Support**: Handles various WhatsApp export formats

## Supported Input Formats

The analyzer supports these WhatsApp-like export formats:

### Format 1: Bracketed with AM/PM

```
[12/03/2023, 9:14 pm] John Doe: Hey there!
[12/03/2023, 9:15 pm] Jane Smith: Hi John, how are you?
```

### Format 2: Dash with 24-hour

```
12/03/2023, 21:14 - John Doe: This is a 24h timestamp format.
12/03/2023, 21:15 - Jane Smith: Works with both formats!
```

### Format 3: With seconds

```
[12/03/2023, 9:14:23 pm] John Doe: Message with seconds
12/03/2023, 21:14:45 - Jane Smith: Also supported
```

## Installation & Setup

### Prerequisites

- Python 3.7+
- Jupyter Notebook or JupyterLab
- Internet connection (for auto-installing dependencies)

### Quick Start

1. **Download the notebook**: `Chatanalyzer.ipynb`
2. **Place your chat export**: Save as `chat.txt` in the same folder
3. **Open in Jupyter**: Run `jupyter notebook` in the folder
4. **Execute all cells**: Kernel → Restart & Run All

### Dependencies

The notebook automatically installs these packages:

- **Core**: `pandas`, `matplotlib`, `seaborn`, `regex`

## Usage

### 1. Prepare Your Data

- Export your chat from WhatsApp: Chat → More → Export Chat
- Save as `chat.txt` in the same folder as the notebook
- Ensure the file uses UTF-8 encoding

### 2. Run the Analysis

- Open `Chatanalyzer.ipynb` in Jupyter
- Run all cells sequentially (top to bottom)
- The notebook will automatically detect and load `chat.txt`

### 3. View Results

The analysis provides:

- **Parsed Data**: Clean table with timestamp, author, message
- **User Activity**: Messages per participant
- **Time Patterns**: Daily timeline and hourly heatmaps
- **Content Insights**: Most frequent words and phrases
- **Sentiment Trends**: Emotional tone analysis by user (if TextBlob available)

## Output Examples

### Message Count by User

```
Messages per author:
John Doe      150
Jane Smith    120
Mike Wilson    85
Name: count, dtype: int64
```

### Activity Heatmap

- Weekday vs. Hour visualization
- Shows when the group is most active
- Helps identify peak conversation times

### Word Frequency

- Top 20 most used words
- Filtered for meaningful content
- Excludes common stopwords

## Customization

### Adding New Chat Formats

If your export uses a different format, modify the regex patterns in the parser:

```python
# Add your custom pattern here
pattern_custom = re.compile(r"your_pattern_here")
```

### Adjusting Date Formats

The parser supports multiple date formats. Add new ones to the `fmt` list:

```python
for fmt in [
    "%d/%m/%Y, %I:%M %p",  # 12/03/2023, 9:14 pm
    "%d/%m/%Y, %H:%M",     # 12/03/2023, 21:14
    # Add your format here
]:
```

### Sentiment Analysis

- **Enable**: Install TextBlob (`pip install textblob`)
- **Customize**: Modify the sentiment calculation logic
- **Export**: Add code to save sentiment results to CSV

## Troubleshooting

### Common Issues

**"File not found" error**

- Ensure `chat.txt` is in the same folder as the notebook
- Check file permissions and encoding

**Parsing fails**

- Verify your chat export format matches supported patterns
- Share a few sample lines for format adaptation
- Check for special characters or encoding issues

**Dependencies not installing**

- Restart Jupyter kernel after installation
- Use `pip install package_name` manually if needed
- Check Python environment and permissions

**Large files slow performance**

- Consider splitting very large exports
- The parser handles multi-line messages efficiently
- Charts may take longer to render with extensive data

### Performance Tips

- **Small chats** (<1000 messages): Runs in seconds
- **Medium chats** (1000-10000 messages): May take 10-30 seconds
- **Large chats** (>10000 messages): Consider data sampling for initial testing

## Advanced Features

### Export Results

Add this code to save your analysis:

```python
# Export parsed data
df.to_csv('parsed_chat.csv', index=False)

# Export analytics
counts_by_author.to_csv('user_counts.csv')
msg_per_day.to_csv('daily_activity.csv')
```

### Custom Visualizations

Extend the notebook with additional charts:

```python
# Message length analysis
df['message_length'] = df['message'].str.len()
df.groupby('author')['message_length'].mean().plot(kind='bar')
```

### Integration with Other Tools

- **Pandas**: Export to Excel, JSON, or databases
- **Plotly**: Interactive visualizations
- **NLTK**: Advanced text processing
- **spaCy**: Named entity recognition

## Contributing

### Adding New Features

1. Fork the repository
2. Create a feature branch
3. Add your improvements
4. Test with various chat formats
5. Submit a pull request

### Reporting Issues

Include:

- Chat export format (first few lines)
- Error messages
- Expected vs. actual behavior
- Python and package versions

## License

This project is open source. Feel free to modify and distribute for personal or educational use.

## Support

For questions or issues:

1. Check the troubleshooting section
2. Review the code comments
3. Test with the sample data first
4. Share specific error details

---

**Happy Analyzing! 🚀**

_Transform your chat logs into meaningful insights with just a few clicks._
