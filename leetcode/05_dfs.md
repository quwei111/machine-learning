# 深度优先搜索

# recursive and nonrecursive

graph1 = {
    'A': ['B', 'S'],
    'B': ['A'],
    'C': ['D', 'E', 'F', 'S'],
    'D': ['C'],
    'E': ['C', 'H'],
    'F': ['C', 'G'],
    'G': ['F', 'S'],
    'H': ['E', 'G'],
    'S': ['A', 'C', 'G']
}


def dfs(graph, node):
    visited = [False] * len(graph)
    dfs_utils(node, visited)


def dfs_utils(graph, node, visited):
    visited[node] = True
    for i in graph[node]:
        if visited[i] == False:
            dfs_utils(graph, i, visited)


def dfs1(graph, node, visited):
    if node not in visited:
        visited.append(node)
        for n in graph[node]:
            dfs1(graph, n, visited)
    return visited


def dfs2(graph, node):
    visited = [node]
    stack = [node]
    while stack:
        node = stack[-1]
        if node not in visited:
            visited.extend(node)
        remove_from_stack = True
        for next in graph[node]:
            if next not in visited:
                stack.extend(next)
                remove_from_stack = False
                break
        if remove_from_stack:
            stack.pop()
    return visited


def dfs_iterative(graph, start_vertex):
    visited = set()
    traversal = []
    stack = [start_vertex]
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            traversal.append(vertex)
            stack.extend(reversed(graph[vertex]))   # add vertex in the same order as visited
    return traversal

if __name__ == '__main__':
    print(dfs(graph1, 'A', []))
    print(dfs2(graph1, 'A'))
