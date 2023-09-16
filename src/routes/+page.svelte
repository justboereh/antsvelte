<script>
	import { Text, Title, Button } from '../lib/index.js';
</script>

<Text>Ant Design (default)</Text>
<Text type="secondary">Ant Design (secondary)</Text>
<Text type="success">Ant Design (success)</Text>
<Text type="warning">Ant Design (warning)</Text>
<Text type="danger">Ant Design (danger)</Text>
<Text disabled>Ant Design (disabled)</Text>
<Text mark>Ant Design (mark)</Text>
<Text code>Ant Design (code)</Text>
<Text keyboard>Ant Design (keyboard)</Text>
<Text underline>Ant Design (underline)</Text>
<Text delete>Ant Design (delete)</Text>
<Text strong>Ant Design (strong)</Text>
<Text italic>Ant Design (italic)</Text>

<Title>h1. Ant Design</Title>
<Title level={2}>h2. Ant Design</Title>
<Title level={3}>h3. Ant Design</Title>
<Title level={4}>h4. Ant Design</Title>
<Title level={5}>h5. Ant Design</Title>

<Button type="primary">Primary Button</Button>
<Button>Default Button</Button>
<Button type="dashed">Dashed Button</Button>
<Button type="text">Text Button</Button>
<Button type="link">Link Button</Button>

<Button>
	<slot name="icon" />

	Search
</Button>
<Button>Search</Button>
<Button>Search</Button>

<Button size="small">Small Button</Button>
<Button>Default Button</Button>
<Button size="large">Large Button</Button>
