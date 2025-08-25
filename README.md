# Capcut[App_Version2.js](https://github.com/user-attachments/files/21961102/App_Version2.js)
import React, { useState } from 'react';
import { View, Text, TextInput, Button, FlatList, StyleSheet } from 'react-native';

export default function App() {
  const [text, setText] = useState('');
  const [items, setItems] = useState([]);

  const addItem = () => {
    if (text.trim()) {
      setItems([...items, { id: Date.now().toString(), value: text }]);
      setText('');
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Danh sách ghi chú</Text>
      <TextInput
        style={styles.input}
        placeholder="Nhập ghi chú..."
        value={text}
        onChangeText={setText}
      />
      <Button title="Thêm" onPress={addItem} />
      <FlatList
        data={items}
        keyExtractor={item => item.id}
        renderItem={({ item }) => <Text style={styles.item}>{item.value}</Text>}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: { flex: 1, padding: 20, marginTop: 40 },
  title: { fontSize: 22, fontWeight: 'bold', marginBottom: 10 },
  input: { borderWidth: 1, borderColor: '#ccc', padding: 8, marginBottom: 10 },
  item: { padding: 10, fontSize: 18, borderBottomWidth: 1, borderColor: '#eee' },
});
