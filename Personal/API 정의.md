
**Input** : 
{
	'language' : {
			'from': 'ko',
			'to': 'en'
	},
	'params': {
		'temperature': 0.0,
		'top_k': 0.1,
		'repetition_penalty': 0.5,
		'presence_penalty': 0.5
	},
	'template': ' your prompt template ',
	'user_instruction': ' your instruction '
}

**Output** : 
{
	'uuid': uuid,
	'content' : {
		'before': 번역 전 원문,
		'after': 번역 후 원문 
	}
}